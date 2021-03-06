---
title       : Titanic Pitch
subtitle    : Exploring Survivorship Rates in Titanic
author      : Stanley Lam
job         : 
framework   : io2012    # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## A Titanic Problem

### Interactive Tool for Exploring Survivorship Rates for the Titanic 
### Stanley Lam

--- .class #id 

## Background and Basic Options
#### The Titanic was a British passenger liner that sank in 1912 after hitting an iceburg. Based on actual survivor data from the Titanic, this tool allows you to calculate your chances of surviving, based on the following three demographic options:

* Gender -- Male/Female
* Age -- Adult/Child
* Ticket Type -- 1st Class/2nd Class/3rd Class/Crew

--- 

## Original Data
#### The survivorship dataset is contained within the R package appropriately titled "datasets". However, the dataset is originally in a 4-dimensional array, which must first be converted to a data frame. The code below shows this conversion (which is done automatically in the app).

```r
library(datasets)
library(plyr)
titanic <- adply(Titanic, c(1,2,3))
head(titanic)
```

```
##   Class    Sex   Age No Yes
## 1   1st   Male Child  0   5
## 2   2nd   Male Child  0  11
## 3   3rd   Male Child 35  13
## 4  Crew   Male Child  0   0
## 5   1st Female Child  0   1
## 6   2nd Female Child  0  13
```

---

## Sample Calculation of Survival Rate

#### The code below shows how the survival rate is calculated. For each passenger type, the number of survivors is divided by the total number of passengers (i.e. the sum of survivors and casualties).

#### The program automatically updates each time the user provides new information.


```r
yes <- titanic$Yes[titanic$Class == "3rd" & titanic$Sex == "Male" & titanic$Age == "Child"]
no <- titanic$No[titanic$Class == "3rd" & titanic$Sex == "Male" & titanic$Age == "Child"]
prob <- yes / (yes + no)
paste(round(100*prob, 2), "%")
```

```
## [1] "27.08 %"
```


---

## Uses

#### This app is beneficial for anyone interested in the Titanic -- from fans looking to deepen their knowledge on the subject to researchers in need of a quick reference. The interface is intuitive and easy-to-use. And best of all, it's free!

#### Alternatively, more information about the original dataset can be found here: http://stat.ethz.ch/R-manual/R-devel/library/datasets/html/Titanic.html
