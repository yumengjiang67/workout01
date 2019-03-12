workout01-yumeng-jiang
================
christine
2019年3月3日

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
shots_data <- read.csv("../data/shots-data.csv",stringsAsFactors = FALSE)
#Effective Shooting % by Player: Overall (i.e. including 2PT and 3PT Field Goals) effective shooting percentage by player, arranged in descending order by percentage

 summarize(group_by(shots_data,name),total=length(name),made=sum(shot_made_flag=="shot_yes"),perc_made=made/total)
```

    ## # A tibble: 5 x 4
    ##   name           total  made perc_made
    ##   <chr>          <int> <int>     <dbl>
    ## 1 Andre Iguodala   371   192     0.518
    ## 2 Graymond Green   578   245     0.424
    ## 3 Kevin Durant     915   495     0.541
    ## 4 Klay Thompson   1220   575     0.471
    ## 5 Stephen Curry   1250   584     0.467

``` r
#2PT Effective Shooting % by Player: 2 PT Field Goal effective shooting percentage by player, arranged in descending order by percentage.
pt2 <- filter(shots_data,shot_type=="2PT Field Goal")
summarize(group_by(pt2,name),total=length(name),made=sum(shot_made_flag=="shot_yes"),perc_made=made/total)
```

    ## # A tibble: 5 x 4
    ##   name           total  made perc_made
    ##   <chr>          <int> <int>     <dbl>
    ## 1 Andre Iguodala   210   134     0.638
    ## 2 Graymond Green   346   171     0.494
    ## 3 Kevin Durant     643   390     0.607
    ## 4 Klay Thompson    640   329     0.514
    ## 5 Stephen Curry    563   304     0.540

``` r
#3PT Effective Shooting % by Player: 3 PT Field Goal effective shooting percentage by player, arranged in descending order by percentage
pt3 <- filter(shots_data,shot_type=="3PT Field Goal")
summarize(group_by(pt3,name),total=length(name),made=sum(shot_made_flag=="shot_yes"),perc_made=made/total)
```

    ## # A tibble: 5 x 4
    ##   name           total  made perc_made
    ##   <chr>          <int> <int>     <dbl>
    ## 1 Andre Iguodala   161    58     0.360
    ## 2 Graymond Green   232    74     0.319
    ## 3 Kevin Durant     272   105     0.386
    ## 4 Klay Thompson    580   246     0.424
    ## 5 Stephen Curry    687   280     0.408

<img src="gsw_shot_charts" width="80%" style="display: block; margin: auto;" />
