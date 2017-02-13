1 - Objective
-------------

LandOcean Energy Services Co., Ltd. (hereafter referred to simply as LandOcean) is a China-based company involved in providing various oil and gas solutions. We are examining the impact of several financial indicators such as rate of return on assets and sales margin, on LandOcean's stock price.

As there are several variables to handle, we will be implementing Principal Component Cnalysis (PCA) to reduce the dimensionality of the dataset and create new uncorrelated variables, so as to ensure an easier process of building the model.

2 - Implementation
------------------

### Importing Stock Price Dataset

    stock = read.csv('stkpc_analysis.csv')

### Principal Component Analysis

    #stock_pca = princomp(stock[, -1])
    #summary(stock_pca)

    pca <- prcomp(stock[2:17],center = TRUE, scale. =TRUE)
    pca2 <- pca <- prcomp(stock[2:17]) #without scaling
    summary(pca2)

    ## Importance of components:
    ##                            PC1     PC2      PC3     PC4     PC5     PC6
    ## Standard deviation     71.6624 43.3849 13.33084 9.79269 0.82403 0.53630
    ## Proportion of Variance  0.7042  0.2581  0.02437 0.01315 0.00009 0.00004
    ## Cumulative Proportion   0.7042  0.9623  0.98666 0.99981 0.99990 0.99994
    ##                            PC7     PC8     PC9   PC10   PC11    PC12
    ## Standard deviation     0.43383 0.35443 0.29950 0.1471 0.1095 0.05253
    ## Proportion of Variance 0.00003 0.00002 0.00001 0.0000 0.0000 0.00000
    ## Cumulative Proportion  0.99996 0.99998 0.99999 1.0000 1.0000 1.00000
    ##                           PC13    PC14    PC15     PC16
    ## Standard deviation     0.04193 0.03893 0.01511 0.008628
    ## Proportion of Variance 0.00000 0.00000 0.00000 0.000000
    ## Cumulative Proportion  1.00000 1.00000 1.00000 1.000000

    print(pca)

    ## Standard deviations:
    ##  [1] 71.662437885 43.384890505 13.330837349  9.792692300  0.824033750
    ##  [6]  0.536300021  0.433830068  0.354428650  0.299495567  0.147109996
    ## [11]  0.109530470  0.052531015  0.041933312  0.038928401  0.015105248
    ## [16]  0.008627849
    ## 
    ## Rotation:
    ##                                                PC1           PC2
    ## rate.of.return.on.total.assets_ROA_A -4.854386e-05 -1.517279e-05
    ## net.assets.income.rateA              -5.892277e-05 -3.541590e-05
    ## operating.profit.ratio               -3.060927e-04 -1.661322e-04
    ## Sales.Margin.rate                    -2.441619e-04 -9.612736e-05
    ## turnover.of.account.receivableA      -6.399202e-02 -9.979213e-01
    ## rate.of.stock.turnoverA              -9.979474e-01  6.399970e-02
    ## velocity.of.liquid.assetsA           -1.127905e-04 -2.938369e-03
    ## turnover.of.total.capitalA            1.145301e-05 -1.726911e-03
    ## liquidity.ratio                       9.005800e-04  4.627333e-03
    ## quick.ratio                          -3.754280e-04  3.825722e-03
    ## asset.liability.ratio                 5.101227e-05 -2.072153e-04
    ## equity.multiplier                     8.341798e-05 -4.947492e-04
    ## Total.Assets.Growth.RateA            -9.340977e-06 -1.349780e-04
    ## net.profit.growth.rateA               2.149796e-03  3.001455e-03
    ## increase.rate.of.business.revenue     4.271403e-04 -4.210751e-04
    ## sustainable.growth.rate              -3.956726e-05 -2.176633e-05
    ##                                                PC3           PC4
    ## rate.of.return.on.total.assets_ROA_A  2.968411e-04 -0.0002912883
    ## net.assets.income.rateA               6.614719e-05 -0.0003835417
    ## operating.profit.ratio                2.275144e-03  0.0020402680
    ## Sales.Margin.rate                     2.843383e-03 -0.0006461738
    ## turnover.of.account.receivableA       5.989802e-03 -0.0032359532
    ## rate.of.stock.turnoverA              -1.866909e-05 -0.0019593436
    ## velocity.of.liquid.assetsA           -8.177722e-03  0.0013448258
    ## turnover.of.total.capitalA           -4.292490e-03  0.0001293768
    ## liquidity.ratio                       7.332268e-01 -0.0122067304
    ## quick.ratio                           6.795623e-01 -0.0125463576
    ## asset.liability.ratio                -5.028642e-03  0.0004079231
    ## equity.multiplier                    -9.445075e-03  0.0013862555
    ## Total.Assets.Growth.RateA            -2.840009e-03 -0.0002176873
    ## net.profit.growth.rateA              -1.747302e-02 -0.9997185914
    ## increase.rate.of.business.revenue    -3.332613e-03 -0.0152498170
    ## sustainable.growth.rate              -1.664611e-04 -0.0008260615
    ##                                                PC5           PC6
    ## rate.of.return.on.total.assets_ROA_A  0.0147854928  0.0028997223
    ## net.assets.income.rateA               0.0260826425  0.0021186855
    ## operating.profit.ratio                0.0772052735  0.0279209465
    ## Sales.Margin.rate                     0.0756105348  0.0392506049
    ## turnover.of.account.receivableA      -0.0001551235  0.0002226327
    ## rate.of.stock.turnoverA               0.0003031057 -0.0009181677
    ## velocity.of.liquid.assetsA           -0.0858874572 -0.1669218347
    ## turnover.of.total.capitalA           -0.0289340371 -0.0712904621
    ## liquidity.ratio                      -0.0419026162 -0.6660075971
    ## quick.ratio                           0.0473186886  0.7160028806
    ## asset.liability.ratio                -0.0156852110  0.0113155714
    ## equity.multiplier                    -0.0399097091  0.0240814322
    ## Total.Assets.Growth.RateA             0.0307926202  0.0262121221
    ## net.profit.growth.rateA              -0.0152303867  0.0002617888
    ## increase.rate.of.business.revenue     0.9857653647 -0.0842539906
    ## sustainable.growth.rate               0.0215017528 -0.0008433393
    ##                                                PC7           PC8
    ## rate.of.return.on.total.assets_ROA_A -0.0082706709 -0.1015482896
    ## net.assets.income.rateA               0.0089336831 -0.1313996128
    ## operating.profit.ratio               -0.0862315164 -0.4004847958
    ## Sales.Margin.rate                    -0.0942957603 -0.3881153246
    ## turnover.of.account.receivableA      -0.0027963327  0.0018510259
    ## rate.of.stock.turnoverA               0.0001551259  0.0003232562
    ## velocity.of.liquid.assetsA            0.6325374355 -0.5190253260
    ## turnover.of.total.capitalA            0.3506956958 -0.2675454391
    ## liquidity.ratio                      -0.0758844282  0.0649302581
    ## quick.ratio                           0.1034788894 -0.0661182806
    ## asset.liability.ratio                 0.2222466804  0.1886107014
    ## equity.multiplier                     0.6106043372  0.5150959188
    ## Total.Assets.Growth.RateA             0.1110826371  0.0354230846
    ## net.profit.growth.rateA              -0.0001403901 -0.0009984249
    ## increase.rate.of.business.revenue     0.0955158229  0.0436524394
    ## sustainable.growth.rate               0.0162813914 -0.0882180990
    ##                                                PC9          PC10
    ## rate.of.return.on.total.assets_ROA_A -0.0810659544  5.693664e-03
    ## net.assets.income.rateA              -0.1349333886  1.668289e-02
    ## operating.profit.ratio               -0.5230592813 -1.174650e-01
    ## Sales.Margin.rate                    -0.5413261183 -1.114198e-01
    ## turnover.of.account.receivableA      -0.0006707626  1.560909e-05
    ## rate.of.stock.turnoverA               0.0002089367  1.650258e-05
    ## velocity.of.liquid.assetsA            0.2651122297  1.285917e-01
    ## turnover.of.total.capitalA            0.1451232931 -2.139615e-01
    ## liquidity.ratio                      -0.0816659240  5.721095e-03
    ## quick.ratio                           0.0882971343 -4.178515e-03
    ## asset.liability.ratio                -0.1391074664  2.655605e-02
    ## equity.multiplier                    -0.4593648769 -2.197168e-01
    ## Total.Assets.Growth.RateA            -0.2305577550  9.278789e-01
    ## net.profit.growth.rateA              -0.0023926583 -3.319883e-04
    ## increase.rate.of.business.revenue     0.0954716538 -1.554084e-02
    ## sustainable.growth.rate              -0.1006997080  3.049312e-02
    ##                                               PC11          PC12
    ## rate.of.return.on.total.assets_ROA_A  8.983790e-02 -0.3251338111
    ## net.assets.income.rateA               1.328305e-01 -0.4723709795
    ## operating.profit.ratio               -5.916761e-02  0.4707143169
    ## Sales.Margin.rate                    -6.133260e-02 -0.1831161135
    ## turnover.of.account.receivableA      -7.550242e-05 -0.0002026475
    ## rate.of.stock.turnoverA               8.088884e-05 -0.0000105016
    ## velocity.of.liquid.assetsA           -4.541269e-01 -0.0361071254
    ## turnover.of.total.capitalA            8.328267e-01  0.1631106278
    ## liquidity.ratio                       1.314710e-02  0.0005202019
    ## quick.ratio                          -1.409462e-02 -0.0006424405
    ## asset.liability.ratio                -3.221463e-02 -0.0706089063
    ## equity.multiplier                    -5.078557e-02  0.0049942035
    ## Total.Assets.Growth.RateA             2.217485e-01  0.1139813736
    ## net.profit.growth.rateA              -5.457432e-04  0.0017086431
    ## increase.rate.of.business.revenue    -2.145517e-02  0.0050633562
    ## sustainable.growth.rate               1.164890e-01 -0.6083664910
    ##                                               PC13          PC14
    ## rate.of.return.on.total.assets_ROA_A  1.747699e-01  1.282839e-01
    ## net.assets.income.rateA               1.492654e-01  2.613575e-01
    ## operating.profit.ratio                2.031051e-01  5.130342e-01
    ## Sales.Margin.rate                    -3.391695e-01 -6.126117e-01
    ## turnover.of.account.receivableA       6.687395e-05  8.773541e-05
    ## rate.of.stock.turnoverA              -3.586001e-05 -3.303497e-05
    ## velocity.of.liquid.assetsA            2.783367e-02 -6.592169e-03
    ## turnover.of.total.capitalA           -8.306479e-02 -6.861026e-02
    ## liquidity.ratio                      -5.448937e-03 -1.201512e-03
    ## quick.ratio                           4.381328e-03  2.741303e-03
    ## asset.liability.ratio                -8.265365e-01  4.451022e-01
    ## equity.multiplier                     2.835713e-01 -1.311589e-01
    ## Total.Assets.Growth.RateA             4.466830e-02 -8.023771e-02
    ## net.profit.growth.rateA               5.440408e-04  1.181995e-03
    ## increase.rate.of.business.revenue    -2.868231e-03 -5.392217e-03
    ## sustainable.growth.rate               1.326093e-01  2.240342e-01
    ##                                               PC15          PC16
    ## rate.of.return.on.total.assets_ROA_A -5.200911e-01 -7.426368e-01
    ## net.assets.income.rateA              -4.528045e-01  6.535181e-01
    ## operating.profit.ratio                8.868705e-02 -2.536565e-02
    ## Sales.Margin.rate                    -9.064930e-03  7.474500e-03
    ## turnover.of.account.receivableA      -3.248893e-05  1.062238e-05
    ## rate.of.stock.turnoverA              -5.328382e-06  2.494015e-06
    ## velocity.of.liquid.assetsA           -3.598887e-03  2.411582e-03
    ## turnover.of.total.capitalA            2.800690e-02 -7.336876e-03
    ## liquidity.ratio                      -1.868625e-03 -1.030588e-03
    ## quick.ratio                           1.914047e-03  9.727647e-04
    ## asset.liability.ratio                -5.463722e-02 -6.549435e-02
    ## equity.multiplier                    -2.044970e-03  7.700448e-03
    ## Total.Assets.Growth.RateA             5.948791e-03 -3.676333e-03
    ## net.profit.growth.rateA              -6.419713e-05  4.254796e-05
    ## increase.rate.of.business.revenue    -2.888808e-03 -2.667484e-03
    ## sustainable.growth.rate               7.160224e-01 -1.275708e-01

We can determine from the summary that the first 4 principal components
(PCs) are sufficient to explain the variance in the variables - 99% to
be precise.

Let us visualize this discovery using a scree plot below.

### Scree Plot

    screeplot(pca2, type = 'l',
              main = 'PCA on Stock Price')

![](README_files/figure-markdown_strict/unnamed-chunk-125-1.png)

As it can be clearly seen in the scree plot, the first 2 PCs explain
most of the variability as there is a sharp kink at PC3 when the line
begins to straighten on the chart.

### Biplot with *ggbiplot* package

    library(ggbiplot)
    s = ggbiplot(pca2, obs.scale = 1, var.scale = 1, 
                 ellipse = T, circle = T)
    print(s + coord_cartesian(xlim = c(-200, 200), ylim = c(-200, 200)))

![](README_files/figure-markdown_strict/unnamed-chunk-126-1.png)

### clustering

    library(devtools)
    install_github("ggbiplot", "vqv")

    ## Warning: Username parameter is deprecated. Please use vqv/ggbiplot

    ## Skipping install of 'ggbiplot' from a github remote, the SHA1 (7325e880) has not changed since last install.
    ##   Use `force = TRUE` to force installation

    stock_price <- stock[,1]

    stock_category <- lapply(stock_price, function(price){
      if(price <= 20){
        return("LOW")
      }else if(price > 20 &  price <= 40 ){
        return ("NORMAL")
      }else if(price > 40  &  price <= 55 ){
        return ("HIGH")
      }else if( price > 55 ){
        return ("V.HIGH")
      }else {
        print("some garbage")
        print(price)
        return(NA)
      }
    })

    stock_category <- as.factor(unlist(stock_category))

    hist(stock_price)

![](README_files/figure-markdown_strict/unnamed-chunk-127-1.png)

    library(ggbiplot)
    g <- ggbiplot(pca, obs.scale = 1, var.scale = 1, 
                  groups = stock_category, ellipse = TRUE, 
                  circle = TRUE)

    g <- g + scale_color_discrete(name = '')
    g <- g + theme(legend.direction = 'horizontal', 
                   legend.position = 'top')
    print(g)

![](README_files/figure-markdown_strict/unnamed-chunk-127-2.png)

### Train-Test Split with *caTools* package

    # install.packages('caTools')
    stock.re <- data.frame(pca$x)
    fit1<- lm(stock_price ~ stock.re$PC1 + stock.re$PC2 + stock.re$PC3 + stock.re$PC4, data=stock.re)
    summary(fit1)

    ## 
    ## Call:
    ## lm(formula = stock_price ~ stock.re$PC1 + stock.re$PC2 + stock.re$PC3 + 
    ##     stock.re$PC4, data = stock.re)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -13.548  -7.192  -2.853   3.778  51.529 
    ## 
    ## Coefficients:
    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  17.486164   0.561516  31.141   <2e-16 ***
    ## stock.re$PC1 -0.017840   0.007848  -2.273   0.0237 *  
    ## stock.re$PC2 -0.029357   0.012963  -2.265   0.0242 *  
    ## stock.re$PC3  0.051025   0.042188   1.209   0.2274    
    ## stock.re$PC4 -0.032004   0.057431  -0.557   0.5777    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 10.01 on 313 degrees of freedom
    ## Multiple R-squared:  0.03713,    Adjusted R-squared:  0.02483 
    ## F-statistic: 3.017 on 4 and 313 DF,  p-value: 0.01826

    #library(caTools)
    #set.seed(123)
    #split = sample.split(stock$`stock price `, SplitRatio = 0.8)
    #trainset = subset(stock, split == T)
    #testset = subset(stock, split == F)

    plot(fit1)

![](README_files/figure-markdown_strict/unnamed-chunk-129-1.png)![](README_files/figure-markdown_strict/unnamed-chunk-129-2.png)![](README_files/figure-markdown_strict/unnamed-chunk-129-3.png)![](README_files/figure-markdown_strict/unnamed-chunk-129-4.png)

### Applying PCA with *caret* package

    # install.packages('caret')
    library(caret)
    #trans = preProcess(trainset[-1], method = c('scale', 'pca'), pcaComp = 2)
    #trainset = predict(trans, trainset)
    #testset = predict(trans, testset)

Generate report rmarkdown::render( input="stock.Rmd",
output\_format="md\_document", output\_file="README.md" )
