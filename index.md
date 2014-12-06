---
title       : Play Data, Play Ball!
subtitle    : NYC Data Science Academy - Winter 2015 CORP-R 002
author      : Summit Suen, Wayne Chen
job         : Etu Taiwan
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- 

## 說到運動資料的分析，你會想到的是...
![](https://www.ocf.berkeley.edu/~superb/pics/moneyball.jpg)

---

## 還是...？

---

## 實務上，

- MLB
- NBA
- NFL
- World Cup 2014
- <del>CPBL</del>

別人在上太空，我們還在殺豬公。

---

## Sabermatrics：賽伯計量學
![](https://bostonu.qualtrics.com/CP/Graphic.php?IM=IM_2h31EGcJG5TEfPf)

Bill James

--- 

## 前人寫扣，後人乘涼


```r
library(Lahman)
library(dplyr)
head(Batting)
```

```
##    playerID yearID stint teamID lgID  G G_batting AB R H X2B X3B HR RBI SB
## 1 aardsda01   2004     1    SFN   NL 11        11  0 0 0   0   0  0   0  0
## 2 aardsda01   2006     1    CHN   NL 45        43  2 0 0   0   0  0   0  0
## 3 aardsda01   2007     1    CHA   AL 25         2  0 0 0   0   0  0   0  0
## 4 aardsda01   2008     1    BOS   AL 47         5  1 0 0   0   0  0   0  0
## 5 aardsda01   2009     1    SEA   AL 73         3  0 0 0   0   0  0   0  0
## 6 aardsda01   2010     1    SEA   AL 53         4  0 0 0   0   0  0   0  0
##   CS BB SO IBB HBP SH SF GIDP G_old
## 1  0  0  0   0   0  0  0    0    11
## 2  0  0  0   0   0  1  0    0    45
## 3  0  0  0   0   0  0  0    0     2
## 4  0  0  1   0   0  0  0    0     5
## 5  0  0  0   0   0  0  0    0    NA
## 6  0  0  0   0   0  0  0    0    NA
```

---

## 前人寫扣，後人繼續乘涼


```r
library(pitchRx)
```

```
## Error in library(pitchRx): there is no package called 'pitchRx'
```

---

## 前人寫扣，後人不能一直乘涼

自己的國家自己救

自己的 crawler/analyzer 自己寫！


---

## 用Ｒ寫爬蟲的屠龍刀


```r
## RSelenium + phantomJS
library(XML)
library(RSelenium)

pJS <- phantom()
Sys.sleep(5)
remDr <- remoteDriver(browserName = 'phantomjs')
remDr$open()

url <- 'http://www.cpbl.com.tw/stats_hr.aspx'
remDr$navigate(url)
```

---


