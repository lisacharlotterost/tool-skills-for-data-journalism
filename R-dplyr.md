
# R: dplyr


Source:
https://rsanchezs.gitbooks.io/dplyr/content/chapter1/groupby.html
http://rpubs.com/justmarkham/dplyr-tutorial and its video: https://www.youtube.com/watch?v=jWjqLW-u3hc


### Preparing the data to make it more readable
```R
# convert to local data frame
# printing only shows 10 rows and as many columns as can fit on your screen
d <- tbl_df(d_old)

# you can specify that you want to see more rows
print(d, n=20)
```


### filter
```R
(d, Month==1, DayofMonth==1)
filter(d, UniqueCarrier=="AA" | UniqueCarrier=="UA") #or
filter(d, UniqueCarrier=="AA", UniqueCarrier=="UA")  #and
filter(d, UniqueCarrier %in% c("AA", "UA")) #good for lots of
```

### select
```R
select(d, DepTime, ArrTime, FlightNum)
select(d, Year:DayofMonth)
select(d, contains("Taxi"))
select(d, starts_with("Delay"), ends_with("ing"), matches("art"))
```
### arrange and sort by
```R
arrange(d, DepDelay)
arrange(d, desc(DepDelay)) #descending
```
### mutate: Add new variables
```R
mutate(d, Speed = Distance/AirTime*60)
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
```

### Misc
- `n()` counts the number of rows in a group
- `n_distinct(vector)` counts the number of unique items in that vector


### What do tildes in ggplot do?
```R
myFormula <- Species ~ Sepal.Length + Petal.Length
# means: "Species depends on Sepal Length and Petal Length

facet_wrap( ~ death )

# means: "All the defined things beforehand in ggplot, depending on the death variable"

facet_grid(. ~ death) # facet into columns
facet_grid(year ~ .) # facet into rows
facet_grid(year ~ deaths) #facet into rows and columns
```
