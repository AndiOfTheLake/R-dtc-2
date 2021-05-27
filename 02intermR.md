---
title: "02 Intermediate R"
author: "Andi"
Last updated: "27 May, 2021"
output: 
  html_document: 
    keep_md: yes
---

## Relational operators


```r
# Comparison of logicals
TRUE == FALSE
```

```
## [1] FALSE
```

```r
# Comparison of numerics
-6*14 != 17 - 101
```

```
## [1] FALSE
```

```r
# Comparison of character strings
"useR" == "user"
```

```
## [1] FALSE
```

```r
# Compare a logical with a numeric
TRUE == 1
```

```
## [1] TRUE
```

```r
# Comparison of numerics
-6 * 5 + 2 >= -10 + 1
```

```
## [1] FALSE
```

```r
# Comparison of character strings
"raining" <= "raining dogs"
```

```
## [1] TRUE
```

```r
# Comparison of logicals
TRUE > FALSE
```

```
## [1] TRUE
```

```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)

# Popular days
linkedin > 15
```

```
## [1]  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE
```

```r
# Quiet days
linkedin <= 5
```

```
## [1] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
```

```r
# LinkedIn more popular than Facebook
linkedin > facebook
```

```
## [1] FALSE  TRUE  TRUE FALSE FALSE  TRUE FALSE
```

## comparing matrices


```r
# The social data has been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)
views <- matrix(c(linkedin, facebook), nrow = 2, byrow = TRUE)

# When does views equal 13?
views == 13
```

```
##       [,1]  [,2]  [,3]  [,4]  [,5]  [,6]  [,7]
## [1,] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
## [2,] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
```

```r
# When is views less than or equal to 14?
views <= 14
```

```
##       [,1] [,2] [,3]  [,4] [,5]  [,6] [,7]
## [1,] FALSE TRUE TRUE  TRUE TRUE FALSE TRUE
## [2,] FALSE TRUE TRUE FALSE TRUE  TRUE TRUE
```

## Logical operators

## & and |


```r
# The linkedin and last variable are already defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
last <- tail(linkedin, 1)

# Is last under 5 or above 10?
last < 5 | last > 10
```

```
## [1] TRUE
```

```r
# Is last between 15 (exclusive) and 20 (inclusive)?
15 < last & last <= 20
```

```
## [1] FALSE
```

```r
# The social data (linkedin, facebook, views) has been created for you

# linkedin exceeds 10 but facebook below 10
linkedin > 10 & facebook < 10
```

```
## [1] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
```

```r
# When were one or both visited at least 12 times?
linkedin >= 12 | facebook >= 12
```

```
## [1]  TRUE FALSE  TRUE  TRUE FALSE  TRUE  TRUE
```

```r
# When is views between 11 (exclusive) and 14 (inclusive)?
views > 11 & views <= 14
```

```
##       [,1]  [,2]  [,3]  [,4]  [,5]  [,6] [,7]
## [1,] FALSE FALSE  TRUE FALSE FALSE FALSE TRUE
## [2,] FALSE FALSE FALSE FALSE FALSE  TRUE TRUE
```

## Blend it all together


```r
# li_df is pre-loaded in your workspace

# Select the second column, named day2, from li_df: second
second <- li_df[, "day2"]

# Build a logical vector, TRUE if value in second is extreme: extremes
extremes <- second > 25 | second <5

# Count the number of TRUEs in extremes
sum(extremes)
```

## Conditonal statements

## if statement

```r
# Variables related to your last day of recordings
medium <- "LinkedIn"
num_views <- 14

# Examine the if statement for medium
if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
}
```

```
## [1] "Showing LinkedIn information"
```

```r
# Write the if statement for num_views
if (num_views > 15){print("You are popular!")}
```

## add an else


```r
# Variables related to your last day of recordings
medium <- "LinkedIn"
num_views <- 14

# Control structure for medium
if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
} else {
  print("Unknown medium")
}
```

```
## [1] "Showing LinkedIn information"
```

```r
# Control structure for num_views
if (num_views > 15) {
  print("You're popular!")
} else {
  print("Try to be more visible!")
}
```

```
## [1] "Try to be more visible!"
```

## further customize: else if


```r
# Variables related to your last day of recordings
medium <- "LinkedIn"
num_views <- 14

# Control structure for medium
if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
} else if (medium == "Facebook") {
  # Add code to print correct string when condition is TRUE
  print("Showing Facebook information")
} else {
  print("Unknown medium")
}
```

```
## [1] "Showing LinkedIn information"
```

```r
# Control structure for num_views
if (num_views > 15) {
  print("You're popular!")
} else if (num_views <= 15 & num_views > 10) {
  # Add code to print correct string when condition is TRUE
  print("Your number of views is average")
} else {
  print("Try to be more visible!")
}
```

```
## [1] "Your number of views is average"
```

## Take control!


```r
# Variables related to your last day of recordings
li <- 15
fb <- 9

# Code the control-flow construct
if (li >= 15 & fb >= 15) {
  sms <- 2 * (li + fb)
} else if (li < 10 & fb < 10) {
  sms <- 0.5 * (li + fb)
} else {
  sms <- li + fb
}

# Print the resulting sms to the console
sms
```

```
## [1] 24
```

