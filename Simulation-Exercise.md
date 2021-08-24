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

 1. A simulation exercise.

    * will compare the exponential distribution in R with the Central Limit Theorem.

 2. Basic inferential data analysis.

    * I will analyze (very basically) the ToothGrowth data in the R datasets package.


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

### Part 2 : Basic inferential data analysis with ToothGrowth dataset


#### ToothGrowth: The Effect of Vitamin C on Tooth Growth in Guinea Pigs

##### Description

###### The response is the length of odontoblasts (cells responsible for tooth growth) in 60 guinea pigs. Each animal received one of three dose
###### levels of vitamin C (0.5, 1, and 2 mg/day) by one of two delivery methods, orange juice or ascorbic acid (a form of vitamin C and coded as VC).


#### Mission

0. Load library's

1. Load the ToothGrowth data and perform some basic exploratory data analyses

2. Provide a basic summary of the data.

3. Use confidence intervals and/or hypothesis tests to compare tooth growth by Supplement and Dose. (Only use the techniques from class, even if there’s other approaches worth considering)

4. State your conclusions and the assumptions needed for your conclusions.


##### Load library's


```r
library(data.table)
library(datasets)
library(ggplot2)
```




##### Load the ToothGrowth data and perform some basic exploratory data analyses


```r
# The Effect of Vitamin C on Tooth Growth in Guinea Pigs
data(ToothGrowth)
toothGrowth <- data.table(ToothGrowth) 
setnames(toothGrowth, c('len','supp','dose'),c('Length','Supplement','Dose'))
toothGrowth$Dose <- as.factor(toothGrowth$Dose)
```
##### As we see, there are 60 observations with 3 variables in this data. Here is a brief explanation of the variables: len denotes the length of the growth, supp represents the delivery (supplement) type (either VC or OJ), and dose denotes the dose in milligrams/day. We change the names of the variables to Length, Supplement, and Dose, respectively.


#### Basic Summary of the data


```r
summary(toothGrowth)
```

```
##      Length      Supplement  Dose   
##  Min.   : 4.20   OJ:30      0.5:20  
##  1st Qu.:13.07   VC:30      1  :20  
##  Median :19.25              2  :20  
##  Mean   :18.81                      
##  3rd Qu.:25.27                      
##  Max.   :33.90
```

```r
head(toothGrowth)
```

```
##    Length Supplement Dose
## 1:    4.2         VC  0.5
## 2:   11.5         VC  0.5
## 3:    7.3         VC  0.5
## 4:    5.8         VC  0.5
## 5:    6.4         VC  0.5
## 6:   10.0         VC  0.5
```


```r
g<-ggplot(ToothGrowth, aes(x=supp, y=len, color=supp)) + geom_boxplot() + facet_grid(facets = ~ dose) + labs(title="Tooth growth by supplement type and dose(mg)" , y = "length", x = "Supplement")
g
```

![](Simulation-Exercise_files/figure-html/unnamed-chunk-8-1.png)<!-- -->














