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

## while loop

## write a while loop


```r
# Initialize the speed variable
speed <- 64

# Code the while loop
while (speed > 30) {
  print("Slow down!")
  speed <- speed - 7
}
```

```
## [1] "Slow down!"
## [1] "Slow down!"
## [1] "Slow down!"
## [1] "Slow down!"
## [1] "Slow down!"
```

```r
# Print out the speed variable
speed
```

```
## [1] 29
```

## Throw in more conditionals


```r
# Initialize the speed variable
speed <- 64

# Extend/adapt the while loop
while (speed > 30) {
  print(paste("Your speed is",speed))
  if (speed > 48) {
    print("Slow down big time!")
    speed = speed - 11
  } else {
    print("Slow down!")
    speed = speed - 6
  }
}
```

```
## [1] "Your speed is 64"
## [1] "Slow down big time!"
## [1] "Your speed is 53"
## [1] "Slow down big time!"
## [1] "Your speed is 42"
## [1] "Slow down!"
## [1] "Your speed is 36"
## [1] "Slow down!"
```

## Stop the while loop: break


```r
# Initialize the speed variable
speed <- 88

while (speed > 30) {
  print(paste("Your speed is", speed))
  
  # Break the while loop when speed exceeds 80
  if (speed > 80) {
  break
  }
  
  if (speed > 48) {
    print("Slow down big time!")
    speed <- speed - 11
  } else {
    print("Slow down!")
    speed <- speed - 6
  }
}
```

```
## [1] "Your speed is 88"
```

## Build a while loop from scratch


```r
# Initialize i as 1 
i <- 1

# Code the while loop
while (i <= 10) {
  print(3*i)
  if (i %% 8 == 0) {
    break
    print(3*i)
  }
  i <- i + 1
}
```

```
## [1] 3
## [1] 6
## [1] 9
## [1] 12
## [1] 15
## [1] 18
## [1] 21
## [1] 24
```

## The for loop

## Loop over a vector


```r
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Loop version 1
for (x in linkedin){
    print(x)
}
```

```
## [1] 16
## [1] 9
## [1] 13
## [1] 5
## [1] 2
## [1] 17
## [1] 14
```

```r
# Loop version 2
for (i in 1: length(linkedin)){
    print(linkedin[i])
}
```

```
## [1] 16
## [1] 9
## [1] 13
## [1] 5
## [1] 2
## [1] 17
## [1] 14
```

## Loop over a list


```r
# The nyc list is already specified
nyc <- list(pop = 8405837, 
            boroughs = c("Manhattan", "Bronx", "Brooklyn", "Queens", "Staten Island"), 
            capital = FALSE)

# Loop version 1
for (x in nyc){
    print(x)
}
```

```
## [1] 8405837
## [1] "Manhattan"     "Bronx"         "Brooklyn"      "Queens"       
## [5] "Staten Island"
## [1] FALSE
```

```r
# Loop version 2
for (i in 1: length(nyc)){
    print(nyc[[i]]) # notice the double square brackets
}
```

```
## [1] 8405837
## [1] "Manhattan"     "Bronx"         "Brooklyn"      "Queens"       
## [5] "Staten Island"
## [1] FALSE
```

## Loop over a matrix


```r
# Define the tic-tac-toe matrix ttt 
ttt<-matrix(c("O",  NA,   "X", NA,  "O",  "O", "X",  NA,   "X" ), 
            byrow = T, nrow = 3);ttt
```

```
##      [,1] [,2] [,3]
## [1,] "O"  NA   "X" 
## [2,] NA   "O"  "O" 
## [3,] "X"  NA   "X"
```

```r
# define the double for loop
for (i in 1: nrow(ttt)) {
  for (j in 1: ncol(ttt)) {
    print(paste("On row", i, "and column", j, "the board contains", ttt[i,j]))
  }
}
```

```
## [1] "On row 1 and column 1 the board contains O"
## [1] "On row 1 and column 2 the board contains NA"
## [1] "On row 1 and column 3 the board contains X"
## [1] "On row 2 and column 1 the board contains NA"
## [1] "On row 2 and column 2 the board contains O"
## [1] "On row 2 and column 3 the board contains O"
## [1] "On row 3 and column 1 the board contains X"
## [1] "On row 3 and column 2 the board contains NA"
## [1] "On row 3 and column 3 the board contains X"
```

## Mix it up with control flow


```r
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Code the for loop with conditionals
for (li in linkedin) {
  if (li > 10) {
    print("You're popular!")    
  } else {
    print("Be more visible!")
  }
  print(li)
}
```

```
## [1] "You're popular!"
## [1] 16
## [1] "Be more visible!"
## [1] 9
## [1] "You're popular!"
## [1] 13
## [1] "Be more visible!"
## [1] 5
## [1] "Be more visible!"
## [1] 2
## [1] "You're popular!"
## [1] 17
## [1] "You're popular!"
## [1] 14
```

## Next, you break it


```r
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Adapt/extend the for loop
for (li in linkedin) {
  if (li > 10) {
    print("You're popular!")
  } else {
    print("Be more visible!")
  }
  
  # Add if statement with break
  if (li > 16){
    print("This is ridiculous, I'm outta here!")
    break
  }
  
  
  # Add if statement with next
  if (li < 5){
    print("This is too embarrassing!")
    next
  }
  

  print(li)
}
```

```
## [1] "You're popular!"
## [1] 16
## [1] "Be more visible!"
## [1] 9
## [1] "You're popular!"
## [1] 13
## [1] "Be more visible!"
## [1] 5
## [1] "Be more visible!"
## [1] "This is too embarrassing!"
## [1] "You're popular!"
## [1] "This is ridiculous, I'm outta here!"
```

```r
# notice that "break" and "next" have to be inside the expression of the for loop
```

## Build a for loop from scratch

This exercise will not introduce any new concepts on for loops.

We already went ahead and defined a variable rquote. This variable has been split up into a vector that contains separate letters and has been stored in a vector chars with the strsplit() function.

Can you write code that counts the number of r's that come before the first u in rquote?


```r
# Pre-defined variables
rquote <- "r's internals are irrefutably intriguing"
chars <- strsplit(rquote, split = "")[[1]]

# Initialize rcount
rcount <- 0

# Finish the for loop
for (char in chars) {
    if (char == "r"){
        rcount = rcount + 1
    }else if (char == "u"){
        break
    }  
  
}

# Print out rcount
print(rcount)
```

```
## [1] 5
```

## Introduction to Functions

## Function documentation

```r
# Consult the documentation on the mean() function
?mean
```

```
## starting httpd help server ... done
```

```r
# Inspect the arguments of the mean() function
args(mean)
```

```
## function (x, ...) 
## NULL
```


## Use a function
Check the documentation on the `mean()` function again:

`?mean`

The Usage section of the documentation includes two versions of the `mean()` function. The first usage,

`mean(x, ...)`

is the most general usage of the mean function. The `'Default S3 method',` however, is:

`mean(x, trim = 0, na.rm = FALSE, ...)`

The `...` is called the ellipsis. It is a way for R to pass arguments along without the function having to name them explicitly. The ellipsis will be treated in more detail in future courses.

For the remainder of this exercise, just work with the second usage of the mean function. Notice that both trim and na.rm have default values. This makes them optional arguments.

```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)

# Calculate the mean of the sum
avg_sum <- mean(linkedin + facebook)

# Calculate the trimmed mean of the sum
avg_sum_trimmed <- mean(linkedin + facebook, trim = 0.2)

# Inspect both new variables
avg_sum
```

```
## [1] 22.28571
```

```r
avg_sum_trimmed
```

```
## [1] 22.6
```

## Nested functions


```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, NA, 17, 14)
facebook <- c(17, NA, 5, 16, 8, 13, 14)

# Calculate the mean absolute deviation
mean(abs(linkedin - facebook), na.rm = T)
```

```
## [1] 4.8
```


