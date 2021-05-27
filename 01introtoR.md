---
title: "Introduction to R"
author: "Andi"
Last updated: "27 May, 2021"
output: 
  html_document: 
    keep_md: yes
---




```r
# Poker winnings from Monday to Friday
poker_vector <- c(140, -50, 20, -120, 240)

# Roulette winnings from Monday to Friday
roulette_vector <- c(-24, -50, 100, -350, 10)

# Assign days as names of poker_vector
names(poker_vector) <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")

# Assign days as names of roulette_vector
names(roulette_vector)<- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")

poker_vector
```

```
##    Monday   Tuesday Wednesday  Thursday    Friday 
##       140       -50        20      -120       240
```



```r
# Poker and roulette winnings from Monday to Friday:
poker_vector <- c(140, -50, 20, -120, 240)
roulette_vector <- c(-24, -50, 100, -350, 10)
days_vector <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
names(poker_vector) <- days_vector
names(roulette_vector) <- days_vector

# Select poker results for Monday, Tuesday and Wednesday
poker_start <- poker_vector[c("Monday", "Tuesday", "Wednesday")]
  
# Calculate the average of the elements in poker_start
mean(poker_start)
```

```
## [1] 36.66667
```


```r
# Poker and roulette winnings from Monday to Friday:
poker_vector <- c(140, -50, 20, -120, 240)
roulette_vector <- c(-24, -50, 100, -350, 10)
days_vector <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
names(poker_vector) <- days_vector
names(roulette_vector) <- days_vector

# Which days did you make money on poker?
selection_vector <- poker_vector > 0
  
# Print out selection_vector
selection_vector
```

```
##    Monday   Tuesday Wednesday  Thursday    Friday 
##      TRUE     FALSE      TRUE     FALSE      TRUE
```


```r
# Poker and roulette winnings from Monday to Friday:
poker_vector <- c(140, -50, 20, -120, 240)
roulette_vector <- c(-24, -50, 100, -350, 10)
days_vector <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
names(poker_vector) <- days_vector
names(roulette_vector) <- days_vector

# Which days did you make money on poker?
selection_vector <- poker_vector > 0

# Select from poker_vector these days
poker_winning_days <- poker_vector[selection_vector]
```


```r
# Poker and roulette winnings from Monday to Friday:
poker_vector <- c(140, -50, 20, -120, 240)
roulette_vector <- c(-24, -50, 100, -350, 10)
days_vector <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
names(poker_vector) <- days_vector
names(roulette_vector) <- days_vector

# Which days did you make money on roulette?
selection_vector <- roulette_vector > 0

# Select from roulette_vector these days
roulette_winning_days <- roulette_vector[selection_vector]
```


```r
# Construct a matrix with 3 rows that contain the numbers 1 up to 9, filled row-wise
matrix(1:9, byrow = TRUE, nrow = 3)
```

```
##      [,1] [,2] [,3]
## [1,]    1    2    3
## [2,]    4    5    6
## [3,]    7    8    9
```

```r
# Box office Star Wars (in millions!)
new_hope <- c(460.998, 314.4)
empire_strikes <- c(290.475, 247.900)
return_jedi <- c(309.306, 165.8)

# Construct matrix
star_wars_matrix <- matrix(c(new_hope, empire_strikes, return_jedi), nrow = 3, byrow = TRUE)

# Vectors region and titles, used for naming
region <- c("US", "non-US")
titles <- c("A New Hope", "The Empire Strikes Back", "Return of the Jedi")

# Name the columns with region
colnames(star_wars_matrix)<-region

# Name the rows with titles
rownames(star_wars_matrix)<-titles

# Print out star_wars_matrix
star_wars_matrix
```

```
##                              US non-US
## A New Hope              460.998  314.4
## The Empire Strikes Back 290.475  247.9
## Return of the Jedi      309.306  165.8
```

## Calculating the worldwide box office


```r
# Construct star_wars_matrix
box_office <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8)
region <- c("US", "non-US")
titles <- c("A New Hope", 
                 "The Empire Strikes Back", 
                 "Return of the Jedi")
               
star_wars_matrix <- matrix(box_office, 
                      nrow = 3, byrow = TRUE,
                      dimnames = list(titles, region))

# Calculate worldwide box office figures
worldwide_vector <- rowSums(star_wars_matrix)
```

## Adding a column for the Worldwide box office


```r
# Construct star_wars_matrix
box_office <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8)
region <- c("US", "non-US")
titles <- c("A New Hope", 
            "The Empire Strikes Back", 
            "Return of the Jedi")
               
star_wars_matrix <- matrix(box_office, 
                      nrow = 3, byrow = TRUE,
                      dimnames = list(titles, region))

# The worldwide box office figures
worldwide_vector <- rowSums(star_wars_matrix)

# Bind the new variable worldwide_vector as a column to star_wars_matrix
all_wars_matrix <- cbind(star_wars_matrix, worldwide_vector)
```

## Adding a row


```r
# Box office Star Wars sequels (in millions!)
The_Phantom_Menace <- c(474.5,  552.5)
Attack_of_the_Clones <- c(310.7,  338.7)
Revenge_of_the_Sith <- c(380.3,  468.5)

# Construct matrix
star_wars_matrix2 <- matrix(c(The_Phantom_Menace, Attack_of_the_Clones, Revenge_of_the_Sith), nrow = 3, byrow = TRUE)

# Vectors region and titles, used for naming
region <- c("US", "non-US")
titles <- c("The Phantom Menace", "Attack of the Clones", "Revenge of the Sith")

# Name the columns with region
colnames(star_wars_matrix2)<-region

# Name the rows with titles
rownames(star_wars_matrix2)<-titles

# Print out star_wars_matrix
star_wars_matrix2
```

```
##                         US non-US
## The Phantom Menace   474.5  552.5
## Attack of the Clones 310.7  338.7
## Revenge of the Sith  380.3  468.5
```

```r
# Combine both Star Wars trilogies in one matrix
all_wars_matrix <- rbind(star_wars_matrix, star_wars_matrix2)
```

## The total box office revenue for the entire saga


```r
# all_wars_matrix is available in your workspace
all_wars_matrix
```

```
##                              US non-US
## A New Hope              460.998  314.4
## The Empire Strikes Back 290.475  247.9
## Return of the Jedi      309.306  165.8
## The Phantom Menace      474.500  552.5
## Attack of the Clones    310.700  338.7
## Revenge of the Sith     380.300  468.5
```

```r
# Total revenue for US and non-US
total_revenue_vector <- colSums(all_wars_matrix)
  
# Print out total_revenue_vector
total_revenue_vector
```

```
##       US   non-US 
## 2226.279 2087.800
```

## Selection of matrix elements


```r
# all_wars_matrix is available in your workspace
all_wars_matrix
```

```
##                              US non-US
## A New Hope              460.998  314.4
## The Empire Strikes Back 290.475  247.9
## Return of the Jedi      309.306  165.8
## The Phantom Menace      474.500  552.5
## Attack of the Clones    310.700  338.7
## Revenge of the Sith     380.300  468.5
```

```r
# Select the non-US revenue for all movies
non_us_all <- all_wars_matrix[,2]
  
# Average non-US revenue
mean(non_us_all)
```

```
## [1] 347.9667
```

```r
# Select the non-US revenue for first two movies
non_us_some <- all_wars_matrix[c(1,2),2]
  
# Average non-US revenue for first two movies
mean(non_us_some)
```

```
## [1] 281.15
```

