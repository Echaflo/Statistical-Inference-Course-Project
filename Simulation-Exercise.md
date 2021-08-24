---
title: "Statistical Inference Course Project"
author: "echf"
date: "23/8/2021"
output:
  html_document: 
    keep_md: true
---

# Synopsis

##### This report is part of Statistical Inference course from Johns Hopkins University (Coursera).

### It consists of two parts:

##### 1. A simulation exercise.

######       will compare the exponential distribution in R with the Central Limit Theorem.

##### 2. Basic inferential data analysis.

######       I will analyze (very basically) the ToothGrowth data in the R datasets package.


### Part 1 : Simulation exercise with exponentials

##### Generate 175 random values from a normal distribution of mean 3 and standard deviation 2 (uses seed 113) 

```r
options(width=80)
set.seed(113) 
datos<-rnorm(175,3,2)
head(datos)
```

```
## [1]  3.2667090  5.7504432  4.4974301  0.4122990  1.8824584 -0.4648985
```
##### Now let's see two important data such as the mean and variance of the data 

```r
mean(datos)
```

```
## [1] 2.892319
```

```r
var(datos)
```

```
## [1] 4.042107
```
##### Now let's see the histogram reflecting the distribution of the information 

```r
 hist(datos)
```

![](Simulation-Exercise_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

##### Relative frequencies are represented and it is possible to make a comparison with the theoretical density function. This comparison is done by executing the following code below. 

```r
 hist(datos, freq=FALSE)
 curve(dnorm(x,3,2),add=TRUE)
```

![](Simulation-Exercise_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

##### From the above we can see how the sample data are distributed against the density they show, so we see the central limit theorem. 

### Part 2 : basic inferential data analysis with ToothGrowth dataset













