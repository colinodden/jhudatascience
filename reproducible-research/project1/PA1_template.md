# Reproducible Research
Colin Odden, colin.odden@osumc.edu  
January 15, 2017  
  


# Exploring Pedometric Data from the _Human Activity Recognition_ Repository

__JHU Data Science Specialization__ - _Reproducible Research_ - Project #1

Author | Email
---|---
Colin Odden | colin.odden@osumc.edu

<!-- Project Requirements -->
<!-- Code for reading in the dataset and/or processing the data -->
<!-- Histogram of the total number of steps taken each day -->
<!-- Mean and median number of steps taken each day -->
<!-- Time series plot of the average number of steps taken -->
<!-- The 5-minute interval that, on average, contains the maximum number of steps -->
<!-- Code to describe and show a strategy for imputing missing data -->
<!-- Histogram of the total number of steps taken each day after missing values are imputed -->
<!-- Panel plot comparing the average number of steps taken per 5-minute interval across weekdays and weekends -->
<!-- All of the R code needed to reproduce the results (numbers, plots, etc.) in the report -->

## Goals

Using pedometric data from the Human Activity Recognition (HAR) repository held at the University of California, Irvine (see _data-description_ below), perform the following operations:

* Compute the mean and median numbers of steps taken per day.
* Plot the distribution of total steps taken each day.
* Show how steps taken varies over the course of an average day.
* Identify and impute missing values where appropriate.
* Plot the distribution of total steps taken each day, using the imputed dataset
* Investigate whether the pattern of steps taken over the course of a day varies by weekdays and weekend days

__Data Description__
These data measure counts of steps taken by a wearer. Counts are provided for 5-minute intervals across several days.

A row comprises a date, identifier indexing the 5-minute interval, and a count of steps within that interval on that day.

N=17568

## Summarizing daily steps taken




The __average__ daily total steps taken is 1.0766\times 10^{4}, and the __median__ daily total steps taken is 1.0765\times 10^{4}.

(_Nota Bene_: This author failed to round values correctly in a couple places. Values are presented in scientific notation in spite of my best efforts... `round(value)' does not round as expected.)

![](PA1_template_files/figure-html/hist1-1.png)<!-- -->


## Average steps taken by 5-min interval within the day

Summing within interval across days allows us to view the pattern of steps taken in the course of an average day.


![](PA1_template_files/figure-html/overday-1.png)<!-- -->




#### Steps-by-interval Maximum

We find that the largest average number of steps is taken in the 104th interval, with an average of 206 steps taken.

## Dealing with missing data

There are 2304 missing values for steps taken, and 0 missing values for date and 0 missing values for interval ID.

For this exercise we will assume that values are missing at random (MAR), and that mean imputation is an acceptable method for imputing missing values. To impute missing values, we will assign the average number of steps taken in that interval across all available days in the data.





The imputed data yield a daily mean of __1.0766\times 10^{4}__ and median of __1.0766189\times 10^{4}__ steps taken. Compared with the original data's mean of 1.0766\times 10^{4} and median of 10765, the imputed data differ by __NA__ and __NA__, respectively. The density of steps by day also differs somewhat:


![](PA1_template_files/figure-html/imputehist-1.png)<!-- -->

## Weekdays vs. Weekends

We ask _is there a difference in activity patterns (as measured by counts of steps through the day), between weekdays and weekend days?_

Toward answering this, we plot the counts of steps, averaged across days, separately for weekdays and weekend days:

![](PA1_template_files/figure-html/weekday_wkend-1.png)<!-- -->

While I do not quantify the difference in this report, visual inspection of the two distributions suggests a meaningfully different temporal pattern to steps taken. Note that steps taken on weekend days are far more evenly distributed through the day, but steps start later (perhaps the subject gets to sleep in a little those days...)
