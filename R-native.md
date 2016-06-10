# R: Native



### Dataframes

You can think of a data frame as something akin to a database table or an Excel spreadsheet. It has a specific number of columns, each of which is expected to contain values of a particular type. It also has an indeterminate number of rows - sets of related values for each column.

```R
#bind variables to a dataframe:
d <- data.frame(weights, prices, types)

#access one column of the dataframe:
d$prices
[1]  9000  5000 12000  7500 18000
```



### Brining data in right format
```R
# Importing data
piracy <- read.csv("piracy.csv")
gdp <- read.table("gdp.txt", sep="  ", header=TRUE)

#Merging
d <- merge(x = gdp, y = piracy)

#change data format
as.integer(d$gdp)
```

### Understanding the data
```r
#show how often an element occurs
> table(d$cat_short)
        bks   blg  isch   nws  shop   vid   web
 8170    35    40  6214   111     8    25 33832

# Barplot this table
> barplot(table(mtcars$cyl))

```

### Plotting

```R
#Plotting GDP against Piracy rate:
> plot(d$GDP, d$Piracy)
```


### Stats

```R
#Finding correlation coefficient:
cor.test(d$GDP, d$Piracy)
-0.8203183

#Calculating the linear model for piracy rate by GDP
#Assign it to the line variable & draw it:
line <- lm(d$Piracy ~ d$GDP)
abline(line)
```
