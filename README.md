1 - Objective
-------------

LandOcean Energy Services Co., Ltd. (hereafter referred to simply as
LandOcean) is a China-based company involved in providing various oil
and gas solutions.

We are examining the impact of several financial indicators such as rate
of return on assets and sales margin, on LandOcean's stock price.

2 - Implementation
------------------

### Importing Stock Price Dataset

    stock = read.csv('stkpc_analysis.csv')

### Principal Component Analysis

    #stock_pca = princomp(stock[, -1])
    #summary(stock_pca)

    pca <- prcomp(stock[2:17],center = TRUE, scale. =TRUE)
    pca2 <-  prcomp(stock[2:17]) #without scaling
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

    ev <- pca$sdev^2


    print(pca)

    ## Standard deviations:
    ##  [1] 2.15261434 1.86361078 1.28698920 1.12791404 1.07534136 1.00219683
    ##  [7] 0.93516720 0.83552939 0.76181748 0.58419554 0.37911364 0.25504843
    ## [13] 0.22085861 0.17649334 0.13388870 0.05466919
    ## 
    ## Rotation:
    ##                                              PC1          PC2          PC3
    ## rate.of.return.on.total.assets_ROA_A -0.44224402  0.073868053 -0.043174643
    ## net.assets.income.rateA              -0.43565462  0.149695050  0.002659954
    ## operating.profit.ratio               -0.41838654  0.011077526  0.035680902
    ## Sales.Margin.rate                    -0.42846830 -0.002899346  0.065164067
    ## turnover.of.account.receivableA      -0.01160320  0.122693913 -0.418485716
    ## rate.of.stock.turnoverA              -0.04008024  0.004083312 -0.050944985
    ## velocity.of.liquid.assetsA            0.01283187  0.358002946 -0.485599640
    ## turnover.of.total.capitalA           -0.01206318  0.352915222 -0.493149821
    ## liquidity.ratio                      -0.09623227 -0.380577724 -0.257872626
    ## quick.ratio                          -0.09877442 -0.379858199 -0.251907833
    ## asset.liability.ratio                 0.17587925  0.405077262  0.157893080
    ## equity.multiplier                     0.15531869  0.372018976  0.122986624
    ## Total.Assets.Growth.RateA            -0.07761889  0.275792499  0.282515485
    ## net.profit.growth.rateA              -0.02705228  0.009669171  0.117144018
    ## increase.rate.of.business.revenue    -0.13920350  0.044294057  0.265758804
    ## sustainable.growth.rate              -0.39208811  0.185697955  0.041263870
    ##                                               PC4         PC5
    ## rate.of.return.on.total.assets_ROA_A  0.068188737 -0.02905737
    ## net.assets.income.rateA              -0.015013679 -0.00753518
    ## operating.profit.ratio               -0.026999228 -0.20332443
    ## Sales.Margin.rate                    -0.044307740 -0.11687588
    ## turnover.of.account.receivableA      -0.008441741  0.13114553
    ## rate.of.stock.turnoverA               0.031405405 -0.30150326
    ## velocity.of.liquid.assetsA            0.054997487  0.05790117
    ## turnover.of.total.capitalA            0.066551697  0.12887644
    ## liquidity.ratio                      -0.492223595  0.14240290
    ## quick.ratio                          -0.497250914  0.13982949
    ## asset.liability.ratio                -0.364983656 -0.02307701
    ## equity.multiplier                    -0.448870363 -0.02581236
    ## Total.Assets.Growth.RateA            -0.373312779  0.01610454
    ## net.profit.growth.rateA               0.117835361  0.72516808
    ## increase.rate.of.business.revenue     0.069246183  0.49018714
    ## sustainable.growth.rate              -0.040478267  0.09269209
    ##                                                PC6         PC7
    ## rate.of.return.on.total.assets_ROA_A  0.0611107801 -0.10640886
    ## net.assets.income.rateA               0.0568129272 -0.08008401
    ## operating.profit.ratio                0.0056663012  0.10788521
    ## Sales.Margin.rate                    -0.0054873697  0.04425377
    ## turnover.of.account.receivableA      -0.3226459373  0.63177769
    ## rate.of.stock.turnoverA              -0.8875467123 -0.23903170
    ## velocity.of.liquid.assetsA            0.0793331553 -0.11919148
    ## turnover.of.total.capitalA            0.1029154149 -0.12331533
    ## liquidity.ratio                       0.0003684995 -0.05787465
    ## quick.ratio                          -0.0111023202 -0.05443203
    ## asset.liability.ratio                -0.0209210029 -0.04543759
    ## equity.multiplier                    -0.0204698080 -0.06714192
    ## Total.Assets.Growth.RateA            -0.0739224460  0.13490381
    ## net.profit.growth.rateA              -0.2370678050 -0.44526908
    ## increase.rate.of.business.revenue    -0.1428725728  0.48488875
    ## sustainable.growth.rate               0.0345297431 -0.13604402
    ##                                               PC8          PC9
    ## rate.of.return.on.total.assets_ROA_A  0.013238171 -0.052477922
    ## net.assets.income.rateA              -0.031542516 -0.003853726
    ## operating.profit.ratio                0.100447467  0.232266574
    ## Sales.Margin.rate                     0.165662149  0.248373225
    ## turnover.of.account.receivableA       0.483158323  0.087846903
    ## rate.of.stock.turnoverA              -0.237868521 -0.043571055
    ## velocity.of.liquid.assetsA           -0.158895648 -0.148714308
    ## turnover.of.total.capitalA           -0.246648374 -0.040999515
    ## liquidity.ratio                      -0.103321855 -0.016083346
    ## quick.ratio                          -0.099180688 -0.013374941
    ## asset.liability.ratio                 0.009547949  0.277643401
    ## equity.multiplier                    -0.017170816  0.408139101
    ## Total.Assets.Growth.RateA             0.170105804 -0.766558077
    ## net.profit.growth.rateA               0.385782903  0.082741331
    ## increase.rate.of.business.revenue    -0.619849608  0.085394502
    ## sustainable.growth.rate              -0.048097287 -0.048282444
    ##                                               PC10         PC11
    ## rate.of.return.on.total.assets_ROA_A  0.2154127359 -0.064677162
    ## net.assets.income.rateA               0.2101199381 -0.028769563
    ## operating.profit.ratio               -0.4634231860 -0.090088410
    ## Sales.Margin.rate                    -0.3721107771 -0.006499780
    ## turnover.of.account.receivableA       0.2154488914  0.020711162
    ## rate.of.stock.turnoverA               0.0065277022 -0.014340430
    ## velocity.of.liquid.assetsA           -0.3697622802  0.641373704
    ## turnover.of.total.capitalA           -0.0506459839 -0.687144201
    ## liquidity.ratio                      -0.0029333815  0.027869909
    ## quick.ratio                          -0.0007036395  0.002570466
    ## asset.liability.ratio                 0.0496292985  0.082148892
    ## equity.multiplier                     0.0519176942 -0.051523858
    ## Total.Assets.Growth.RateA            -0.1956097315 -0.123980927
    ## net.profit.growth.rateA              -0.1688518388 -0.030812258
    ## increase.rate.of.business.revenue    -0.1007815601  0.037626732
    ## sustainable.growth.rate               0.5370017154  0.273397334
    ##                                              PC12         PC13
    ## rate.of.return.on.total.assets_ROA_A  0.635410276  0.120478457
    ## net.assets.income.rateA               0.217020490  0.247643935
    ## operating.profit.ratio               -0.068268957 -0.030453768
    ## Sales.Margin.rate                    -0.270273199 -0.045871647
    ## turnover.of.account.receivableA       0.029578263  0.007699905
    ## rate.of.stock.turnoverA              -0.006514900  0.004930651
    ## velocity.of.liquid.assetsA            0.107120965 -0.033758040
    ## turnover.of.total.capitalA           -0.211078200 -0.009601974
    ## liquidity.ratio                      -0.009986703  0.031331071
    ## quick.ratio                           0.003147158  0.060628996
    ## asset.liability.ratio                -0.151678227  0.708043836
    ## equity.multiplier                     0.303440000 -0.585460717
    ## Total.Assets.Growth.RateA            -0.008829424 -0.064676701
    ## net.profit.growth.rateA               0.029325393  0.008604606
    ## increase.rate.of.business.revenue     0.049773504  0.009210710
    ## sustainable.growth.rate              -0.543961685 -0.258303295
    ##                                              PC14         PC15
    ## rate.of.return.on.total.assets_ROA_A -0.207862646  0.510440305
    ## net.assets.income.rateA               0.169975517 -0.770801081
    ## operating.profit.ratio                0.655401884  0.218117691
    ## Sales.Margin.rate                    -0.691637868 -0.114230198
    ## turnover.of.account.receivableA       0.009620330 -0.011022674
    ## rate.of.stock.turnoverA              -0.011949509 -0.005774755
    ## velocity.of.liquid.assetsA           -0.011551844 -0.023103146
    ## turnover.of.total.capitalA           -0.038955691  0.042306806
    ## liquidity.ratio                       0.033550027 -0.007995366
    ## quick.ratio                          -0.014141600  0.034330425
    ## asset.liability.ratio                -0.013632798  0.180231281
    ## equity.multiplier                    -0.007302468 -0.089972506
    ## Total.Assets.Growth.RateA            -0.017478632  0.007003499
    ## net.profit.growth.rateA               0.071800435  0.002769287
    ## increase.rate.of.business.revenue    -0.032397847  0.026965094
    ## sustainable.growth.rate               0.100126657  0.199020981
    ##                                               PC16
    ## rate.of.return.on.total.assets_ROA_A -0.0318725332
    ## net.assets.income.rateA               0.0206583244
    ## operating.profit.ratio                0.0136487505
    ## Sales.Margin.rate                    -0.0185291086
    ## turnover.of.account.receivableA      -0.0036020410
    ## rate.of.stock.turnoverA              -0.0066819873
    ## velocity.of.liquid.assetsA            0.0159607367
    ## turnover.of.total.capitalA           -0.0083604099
    ## liquidity.ratio                      -0.7067524860
    ## quick.ratio                           0.7053437446
    ## asset.liability.ratio                -0.0202666990
    ## equity.multiplier                     0.0079602403
    ## Total.Assets.Growth.RateA            -0.0040199310
    ## net.profit.growth.rateA               0.0006675884
    ## increase.rate.of.business.revenue    -0.0026678458
    ## sustainable.growth.rate               0.0117809962

We can determine from the summary that the first 4 principal components
(PCs) are sufficient to explain the variance in the variables - 99% to
be precise.

Let us visualize this discovery using a scree plot below.

### Scree Plot

    screeplot(pca2, type = 'l',
              main = 'PCA on Stock Price')

![](README_files/figure-markdown_strict/unnamed-chunk-18-1.png)

As it can be clearly seen in the scree plot, the first 2 PCs explain
most of the variability as there is a sharp kink at PC3 when the line
begins to straighten on the chart.

### Biplot with *ggbiplot* package

    library(ggbiplot)
    s = ggbiplot(pca2, obs.scale = 1, var.scale = 1, 
                 ellipse = T, circle = T)
    print(s + coord_cartesian(xlim = c(-200, 200), ylim = c(-200, 200)))

![](README_files/figure-markdown_strict/unnamed-chunk-19-1.png)

### clustering

    library(devtools)
    #install_github("ggbiplot", "vqv")
     
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

![](README_files/figure-markdown_strict/unnamed-chunk-20-1.png)

    library(ggbiplot)
    g <- ggbiplot(pca, obs.scale = 1, var.scale = 1, 
                  groups = stock_category, ellipse = TRUE, 
                  circle = TRUE)

    g <- g + scale_color_discrete(name = '')
    g <- g + theme(legend.direction = 'horizontal', 
                   legend.position = 'top')
    print(g)

![](README_files/figure-markdown_strict/unnamed-chunk-20-2.png)

### Train-Test Split with *caTools* package

    # install.packages('caTools')
    stock.re <- data.frame(pca$x)
    fit1<- lm(stock_price ~ stock.re$PC1 + stock.re$PC2 + stock.re$PC3 + stock.re$PC4 + stock.re$PC5 + stock.re$PC6, data=stock.re)
    summary(fit1)

    ## 
    ## Call:
    ## lm(formula = stock_price ~ stock.re$PC1 + stock.re$PC2 + stock.re$PC3 + 
    ##     stock.re$PC4 + stock.re$PC5 + stock.re$PC6, data = stock.re)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -18.839  -6.766  -2.134   4.499  49.698 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   17.4862     0.5298  33.005  < 2e-16 ***
    ## stock.re$PC1  -1.5872     0.2465  -6.439 4.57e-10 ***
    ## stock.re$PC2   0.3690     0.2847   1.296  0.19592    
    ## stock.re$PC3   0.1370     0.4123   0.332  0.73983    
    ## stock.re$PC4  -0.6799     0.4705  -1.445  0.14939    
    ## stock.re$PC5   0.5311     0.4935   1.076  0.28268    
    ## stock.re$PC6  -1.4644     0.5295  -2.766  0.00602 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 9.448 on 311 degrees of freedom
    ## Multiple R-squared:  0.1483, Adjusted R-squared:  0.1318 
    ## F-statistic: 9.024 on 6 and 311 DF,  p-value: 4.228e-09

    #library(caTools)
    #set.seed(123)
    #split = sample.split(stock$`stock price `, SplitRatio = 0.8)
    #trainset = subset(stock, split == T)
    #testset = subset(stock, split == F)

    plot(fit1)

![](README_files/figure-markdown_strict/unnamed-chunk-22-1.png)![](README_files/figure-markdown_strict/unnamed-chunk-22-2.png)![](README_files/figure-markdown_strict/unnamed-chunk-22-3.png)![](README_files/figure-markdown_strict/unnamed-chunk-22-4.png)

### Applying PCA with *caret* package

    # install.packages('caret')
    library(caret)
    #trans = preProcess(trainset[-1], method = c('scale', 'pca'), pcaComp = 2)
    #trainset = predict(trans, trainset)
    #testset = predict(trans, testset)

Generate report rmarkdown::render( input="stock.Rmd",
output\_format="md\_document", output\_file="README.md" )
