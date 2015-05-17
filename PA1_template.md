# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

We begin by reading the supplied activity data from a file in CSV format and then extracting a subset containing only the complete cases for the initial calculations.  Later the missing values will be interpolated with imputed values but for now we'll ignore the missing values.


```r
activity <- read.csv("data/activity.csv")
activity.nona <- activity[complete.cases(activity),]
```

## What is mean total number of steps taken per day?

The total steps per day is calculated as follows:

```r
steps.by.day <- split(activity.nona, activity.nona$date)
total.steps.by.day <- lapply(steps.by.day, function(x) sum(x[["steps"]]))
```

The mean steps per day is calculated as follows:

```r
mean.steps.per.day <- mean(unlist(total.steps.by.day))
mean.steps.per.day
```

```
## [1] 9354.23
```

The median steps per day is calculated as follows:

```r
median.steps.per.day <- median(unlist(total.steps.by.day))
median.steps.per.day
```

```
## [1] 10395
```

## What is the average daily activity pattern?



```r
steps.by.interval <- split(activity.nona, activity.nona$interval)
mean.steps.by.interval <- lapply(steps.by.interval, function(x) mean(x[["steps"]]))
plot(names(mean.steps.by.interval), mean.steps.by.interval, type="l",
     xlab="Time-of-Day Interval", ylab="Steps Averaged Across Days")
```

![](PA1_template_files/figure-html/unnamed-chunk-5-1.png) 

## Imputing missing values




## Are there differences in activity patterns between weekdays and weekends?



