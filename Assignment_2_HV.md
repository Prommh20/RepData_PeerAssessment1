---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data
The following code shows how the data was imported.

```r
data <- read.csv('activity.csv')
```

## Histogram showing the total number of steps taken everyday
The following code was used to determine the total number of steps per day

```r
agg <- aggregate(steps~date,data,sum)
hist(agg$steps)
```

![](Assignment_2_HV_files/figure-html/histogram-1.png)<!-- -->

## What is mean total number of steps taken per day?

```r
meansteps <- mean(agg$steps)
mediansteps <- median(agg$steps)
```
The mean number of steps per day is 10766.19 and the median number of steps is 10765.  

## What is the average daily activity pattern?
The following code is used to determine the average number of steps per 5-min interval and plots the resulting data

```r
dayagg <- aggregate(steps~interval,data,mean)
plot(dayagg$interval,dayagg$steps,type = "l",xlab='Time of day',ylab='Average numbr of steps', main='Average daily number of steps per 5-min interval')
```

![](Assignment_2_HV_files/figure-html/unnamed-chunk-2-1.png)<!-- -->


## Imputing missing values
All missing values were imputed by replacing NA with zero. The code below shows how this was done.

```r
data[is.na(data)] = 0
```


## Are there differences in activity patterns between weekdays and weekends?
