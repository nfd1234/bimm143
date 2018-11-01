lecture05
================
Nicholas Donahue
11/1/2018

``` r
weight<- read.table("bimm143_05_rstats/weight_chart.txt", header = TRUE)
#
plot(weight$Age, weight$Weight, typ="o", pch=15, cex=1.5, lwd=2, ylim=c(2,10), xlab="Age (months)", ylab="Weight (kg)", main="Baby weight with age") 
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-1.png)

``` r
#barplot
mouse <- read.table("bimm143_05_rstats/feature_counts.txt", sep="\t", header=TRUE)
par(mar=c(3.1, 11.1, 4.1, 2))
barplot(mouse$Count, names.arg=mouse$Feature, 
        horiz=TRUE, ylab="", 
        main="Number of features in the mouse GRCm38 genome", 
        las=1, xlim=c(0,80000))
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-2.png)

``` r
#histogram
hist(c(rnorm(100000), rnorm(100000)+4))
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-3.png)

``` r
#plot characters
plot( 1:5, pch=1:5, cex=1:5 )
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-4.png)

``` r
#recycling
plot( 1:10, pch=1:5, cex=1:5, col=c("red", "blue", "green") )
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-5.png)

``` r
#Boxplot
boxplot( cbind( rnorm(1000,0), rnorm(1000,4) ) )
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-6.png)

``` r
#color in plots
mf<-read.delim("bimm143_05_rstats/male_female_counts.txt", sep="\t", header=TRUE)
barplot(mf$Count, names.arg = mf$Sample, las=2, col=rainbow(nrow(mf)))
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-7.png)

``` r
barplot(mf$Count, names.arg = mf$Sample, las=2, col=c("red", "blue"))
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-8.png)

``` r
#3B Coloring by Value
genes<-read.delim("bimm143_05_rstats/up_down_expression.txt")
#how many genes in dataset
nrow(genes)
```

    ## [1] 5196

``` r
#how many are up, down and all around
table(genes$State)
```

    ## 
    ##       down unchanging         up 
    ##         72       4997        127

``` r
#plot of data
palette(c("blue","gray","red"))
plot(genes$Condition1, genes$Condition2, col=genes$State)
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-9.png)

``` r
#dynamic use of color
meth <- read.delim("bimm143_05_rstats/expression_methylation.txt")
plot(meth$gene.meth, meth$expression)
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-10.png)

``` r
#
mycols <- densCols(meth$gene.meth, meth$expression)
plot(meth$gene.meth, meth$expression, col=mycols)
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-11.png)

``` r
#
inds <- meth$expression>0
mycols2 <- densCols(meth$gene.meth[inds], meth$expression[inds], colramp = colorRampPalette(c("blue2", "green2", "red2", "yellow")))
plot(meth$gene.meth[inds], meth$expression[inds], col=mycols2, pch=20)
```

![](rmarkdown_lecture_5_files/figure-markdown_github/unnamed-chunk-1-12.png)

``` r
#Exercise 4 Revisted
```
