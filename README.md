
<!-- README.md is generated from README.Rmd. Please edit the README.Rmd file -->

# Lab report \#2

## Blake, Amaya, Brietta, Simeon

Follow the instructions posted at
<https://ds202-at-isu.github.io/labs.html> for the lab assignment. The
work is meant to be finished during the lab time, but you have time
until Monday evening to polish things.

Include your answers in this document (Rmd file). Make sure that it
knits properly (into the md file). Upload both the Rmd and the md file
to your repository.

All submissions to the github repo will be automatically uploaded for
grading once the due date is passed. Submit a link to your repository on
Canvas (only one submission per team) to signal to the instructors that
you are done with your submission.

``` r
library(classdata) # Simeon
library(ggplot2) # Blake
```

1.  inspect the first few lines of the data set:

what variables are there? of what type are the variables? what does each
variable mean? what do we expect their data range to be?

The 16 variables are:

``` r
str(ames) #blake
```

    ## tibble [6,935 × 16] (S3: tbl_df/tbl/data.frame)
    ##  $ Parcel ID            : chr [1:6935] "0903202160" "0907428215" "0909428070" "0923203160" ...
    ##  $ Address              : chr [1:6935] "1024 RIDGEWOOD AVE, AMES" "4503 TWAIN CIR UNIT 105, AMES" "2030 MCCARTHY RD, AMES" "3404 EMERALD DR, AMES" ...
    ##  $ Style                : Factor w/ 12 levels "1 1/2 Story Brick",..: 2 5 5 5 NA 9 5 5 5 5 ...
    ##  $ Occupancy            : Factor w/ 5 levels "Condominium",..: 2 1 2 3 NA 2 2 1 2 2 ...
    ##  $ Sale Date            : Date[1:6935], format: "2022-08-12" "2022-08-04" ...
    ##  $ Sale Price           : num [1:6935] 181900 127100 0 245000 449664 ...
    ##  $ Multi Sale           : chr [1:6935] NA NA NA NA ...
    ##  $ YearBuilt            : num [1:6935] 1940 2006 1951 1997 NA ...
    ##  $ Acres                : num [1:6935] 0.109 0.027 0.321 0.103 0.287 0.494 0.172 0.023 0.285 0.172 ...
    ##  $ TotalLivingArea (sf) : num [1:6935] 1030 771 1456 1289 NA ...
    ##  $ Bedrooms             : num [1:6935] 2 1 3 4 NA 4 5 1 3 4 ...
    ##  $ FinishedBsmtArea (sf): num [1:6935] NA NA 1261 890 NA ...
    ##  $ LotArea(sf)          : num [1:6935] 4740 1181 14000 4500 12493 ...
    ##  $ AC                   : chr [1:6935] "Yes" "Yes" "Yes" "Yes" ...
    ##  $ FirePlace            : chr [1:6935] "Yes" "No" "No" "No" ...
    ##  $ Neighborhood         : Factor w/ 42 levels "(0) None","(13) Apts: Campus",..: 15 40 19 18 6 24 14 40 13 23 ...

``` r
colnames(ames)#blake
```

    ##  [1] "Parcel ID"             "Address"               "Style"                
    ##  [4] "Occupancy"             "Sale Date"             "Sale Price"           
    ##  [7] "Multi Sale"            "YearBuilt"             "Acres"                
    ## [10] "TotalLivingArea (sf)"  "Bedrooms"              "FinishedBsmtArea (sf)"
    ## [13] "LotArea(sf)"           "AC"                    "FirePlace"            
    ## [16] "Neighborhood"

``` r
head(ames)#brietta
```

    ## # A tibble: 6 × 16
    ##   `Parcel ID` Address      Style Occupancy `Sale Date` `Sale Price` `Multi Sale`
    ##   <chr>       <chr>        <fct> <fct>     <date>             <dbl> <chr>       
    ## 1 0903202160  1024 RIDGEW… 1 1/… Single-F… 2022-08-12        181900 <NA>        
    ## 2 0907428215  4503 TWAIN … 1 St… Condomin… 2022-08-04        127100 <NA>        
    ## 3 0909428070  2030 MCCART… 1 St… Single-F… 2022-08-15             0 <NA>        
    ## 4 0923203160  3404 EMERAL… 1 St… Townhouse 2022-08-09        245000 <NA>        
    ## 5 0520440010  4507 EVERES… <NA>  <NA>      2022-08-03        449664 <NA>        
    ## 6 0907275030  4512 HEMING… 2 St… Single-F… 2022-08-16        368000 <NA>        
    ## # ℹ 9 more variables: YearBuilt <dbl>, Acres <dbl>,
    ## #   `TotalLivingArea (sf)` <dbl>, Bedrooms <dbl>,
    ## #   `FinishedBsmtArea (sf)` <dbl>, `LotArea(sf)` <dbl>, AC <chr>,
    ## #   FirePlace <chr>, Neighborhood <fct>

\#brietta

Numerical - 7

Strings/Character - 5

Factor - 3

Date - 1

- Parcel ID - Numerical

  general number given for the listing - range could be any number
  following numerically after the previous one - incremented

- Address - String

  could be any combination of numbers and letters based on the address

- Style - Factor

  descriptor for the house - range could be anything descriptive for the
  house or apartment

- Occupancy - Factor

  same as above but describes how many people and what type of building
  it is - ex condo

- Sale Date - Date

  range is any date that the thing was purchased - range is any logical
  date

- Sale Price - Numerical

  no range for sale proce

- Multi Sale - String

  if there was more than one building purchaed - NA or other input

- YearBuilt - Numerical

  has to be wihtin a range of years that is logical

- Acres - Numerical

  any number - has to make sense

- TotalLivingArea (sf) - Numerical

  same as acres

- Bedrooms - Numerical

  whole number - also has to be a logical number

- FinishedBsmtArea (sf) - Numerical

  area of the basement - should be around the same as living area

- LotArea(sf) - Numerical

  same as basement - area of loft - should be around the same area as
  the living area

- AC - String

  yes or no for AC

- FirePlace - String

  yes or no for fireplace

- Neighborhood - Factor

  descriptor for describing the area - no range

2.  is there a variable of special interest or focus? \# Simeon The
    variable of interest is Sale Price

3.  start the exploration with the main variable:

- what is the range of the variable? draw a histogram for a numeric
  variable or a bar chart, if the variable is categorical. what is the
  general pattern? is there anything odd?
- follow-up on oddities: see 4

The range of the Sale Price is: 0 - 20500000

(Range code shown twice)

``` r
  range(ames$`Sale Price`, na.rm = TRUE) #Amaya
```

    ## [1]        0 20500000

``` r
  range(ames$`Sale Price`) #blake
```

    ## [1]        0 20500000

Histogram

``` r
  hist(ames$`Sale Price`, main = "Histogram of Sale Prices", xlab = "Sale Price", breaks = 30)
```

![](README_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
#Amaya
```

Oddities:

Its odd that there are two bars off in the far right. They are outliers
of sales prices showing that a few houses were sold and bought for a
large amount of money compared to the majority of the houses. Most of
the proces are below \$500,000 - leaning more towards 100,000 - 200,000
range.

4.  pick a variable that might be related to the main variable. \#Simeon

``` r
range(ames$`Sale Date`)
```

    ## [1] "2017-07-03" "2022-08-31"

- what is the relationship to the main variable? plot a scatterplot,
  boxplot or facetted barcharts (dependening on the types of variables
  involved). Describe overall pattern, does this variable describe any
  oddities discovered in 3? Identify/follow-up on any oddities.

``` r
ames$`Sale Date` <- as.Date(ames$`Sale Date`)
plot(ames$`Sale Date`, ames$`Sale Price`, 
     main = "Scatter Plot of Sale Date vs. Sale Price", 
     xlab = "Sale Date", 
     ylab = "Sale Price", 
     col = "blue", 
     pch = 19)
```

![](README_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

4.  pick a variable that might be related to the main variable.
    \#Brietta

- what is the range of that variable? plot. describe the pattern.

Range:

``` r
  mean(ames$"TotalLivingArea",na.rm = TRUE)
```

    ## Warning: Unknown or uninitialised column: `TotalLivingArea`.

    ## Warning in mean.default(ames$TotalLivingArea, na.rm = TRUE): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

``` r
  range(ames$"TotalLivingArea",na.rm = TRUE)
```

    ## Warning: Unknown or uninitialised column: `TotalLivingArea`.

    ## Warning in min(x, na.rm = na.rm): no non-missing arguments to min; returning
    ## Inf

    ## Warning in max(x, na.rm = na.rm): no non-missing arguments to max; returning
    ## -Inf

    ## [1]  Inf -Inf

the range is 0 - 6007

Plot:

``` r
library(ggplot2)
```

``` r
livingArea = ames$`TotalLivingArea (sf)`
price = ames$`Sale Price`
ggplot(aes( x = livingArea, y = price),data = ames)+geom_line()
```

    ## Warning: Removed 447 rows containing missing values or values outside the scale range
    ## (`geom_line()`).

![](README_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

There is a weird relationship between price and living area. There are
some high priced buildings with low square feet and high square feet
buildings at a relatively low price. One theory is that the high priced
areas are a part of a bigger building like a condo or apartment and it
could be the price for the whole building and the living area of one of
the apartments.

- what is the relationship to the main variable? plot a scatterplot,
  boxplot or facetted barcharts (dependening on the types of variables
  involved). Describe overall pattern, does this variable describe any
  oddities discovered in 3? Identify/follow-up on any oddities.

``` r
ggplot(aes( x = livingArea, y = price),data = ames)+geom_point()
```

    ## Warning: Removed 447 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
#other options
#ggplot(aes( x = livingArea, y = price),data = ames)+geom_boxplot() #no - doesnt work
#ggplot(aes( x = livingArea, y = price),data = ames)+geom_bar() #no - have x and y
```

This is a better visual of the graph above - the dots are easier to see
than the lines that crowd the screen. I still have the same reasoning as
above in terms of the relationships between the variables.

The only description of the oddities in 3 that this would explain is
that we can see how many expensive houses there are. Based on the high
concentration of dots lower demonstrating cheaper houses and the low
concentration of the dots on the expensive houses.

4.  pick a variable that might be related to the main variable.  
    \#Blake Acres

``` r
#The range of the acreage is shown in the boxplot that follows:
ggplot(ames, aes(x=Acres))+
  geom_boxplot()
```

    ## Warning: Removed 89 rows containing non-finite outside the scale range
    ## (`stat_boxplot()`).

![](README_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

There is a large group of acreage that is near 0, with some that grow
higher and some high outliers

``` r
ggplot(ames, aes(x=Acres,y=`Sale Price`))+
  geom_point()
```

    ## Warning: Removed 89 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-12-1.png)<!-- --> It is hard
to tell a strong correlation between the 2 data sets, because there is a
large bunch of data with a low price and low acreage (as seen in the
plot). However, there does seem to be a grouping near the origin of the
chart.
