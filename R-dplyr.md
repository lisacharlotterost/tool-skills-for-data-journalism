
# R: dplyr


Source:
https://rsanchezs.gitbooks.io/dplyr/content/chapter1/groupby.html
http://rpubs.com/justmarkham/dplyr-tutorial and its video: https://www.youtube.com/watch?v=jWjqLW-u3hc
http://rpubs.com/justmarkham/dplyr-tutorial-part-2


### Preparing the data to make it more readable & display the data
```R
# convert to local data frame
# printing only shows 10 rows and as many columns as can fit on your screen
d <- tbl_df(d_old)

# you can specify that you want to see more rows
print(d, n=20)

# if you don't want to prepare the data, add to each pipeline:
mtcars %>% head()

```


### filter
```R
(d, Month==1, DayofMonth==1)
# or:
filter(d, UniqueCarrier=="AA" | UniqueCarrier=="UA")
# and:
filter(d, UniqueCarrier=="AA", UniqueCarrier=="UA")  
# good for lots of different variables:
filter(d, UniqueCarrier %in% c("AA", "UA"))

# determing if numeric values fall in a range
d %>% filter(between(dep_time, 600, 605))

# select all dep times without NAs
d %>% filter(!is.na(dep_time))

# slice() filters rows by position:
d %>% slice(1000:1005)

# keep the first three rows within each group:
d %>% group_by(month, day) %>% slice(1:3)

# sample three rows from each group
d %>% group_by(month, day) %>% sample_n(3)

# keep three rows from each group with the top dep_delay
d %>%
  group_by(month, day) %>%
  top_n(3, dep_delay)

```

### select
```R
select(d, DepTime, ArrTime, FlightNum)
select(d, Year:DayofMonth)
select(d, contains("Taxi"))
select(d, starts_with("Delay"), ends_with("ing"), matches("art"))

# hide columns
select(d, -(contains("Taxi")))
select(d, -DepTime, -ArrTime)

# select() can be used to rename columns, though all columns not mentioned are dropped
d %>% select(tail = tailnum)

# unique rows:
flights %>% select(origin, dest) %>% distinct()


```

### rename

```r
# rename() does the same thing as select(tail=tailnum), except all columns not mentioned are kept
d %>% rename(tail = tailnum)

```

### arrange and sort by
```R
arrange(d, DepDelay)
arrange(d, desc(DepDelay)) #descending
```


### mutate: Add new variables
```R
mutate(d, Speed = Distance/AirTime*60)

# transmute() only keeps the new variables:
d %>% transmute(speed = distance/air_time*60)

```


### summarise: Reduce variables to values
```R
summarise(d, avg_delay = mean(ArrDelay, na.rm=TRUE))

# for each carrier, calculate the percentage of flights cancelled or diverted (apply the means to Cancelled and Diverted)
d %>%
    group_by(UniqueCarrier) %>%
    summarise_each(funs(mean), Cancelled, Diverted)

# for each carrier, calculate the minimum and maximum arrival and departure delays (apply both functions to every column that matches "Delay".
# the dot stands for all the columns to which the functions in funs are applied
d %>%
    group_by(UniqueCarrier) %>%
    summarise_each(funs(min(., na.rm=TRUE), max(., na.rm=TRUE)), matches("Delay"))


# all the following commands do the same thing:
d %>% group_by(month) %>% summarise(cnt = n()) %>% arrange(desc(cnt))
d %>% group_by(month) %>% tally(sort=TRUE)
d %>% count(month,sort=TRUE)

# n_groups() simply reports the number of groups
flights %>% group_by(month) %>% n_groups()

```

### Misc
- `n()` counts the number of rows in a group
- `n_distinct(vector)` counts the number of unique items in that vector
