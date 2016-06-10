# R

###Vectors

Assign values to a vector. Then give each value a name/label. If you `barplot`the vector, the label will appear in the plot:

```R
> x <- c(1,6,7,2,5)
> names(x) <- c("eins","2", "drei", "vier", "fünf")
> barplot(x)
```

```R
> barplot(1:100) #plots 100 bars from 1 to 100
> barplot(x+20) #plots x plus 20 on every value
```

###Factors
Often your data needs to be grouped by category: blood pressure by age range, accidents by auto manufacturer, and so forth. R has a special collection type called a factor to track these categorized values.

In the following case, R finds automatically multiple entries and can display them with `levels(...)`:

```R
> chests <- c('gold', 'silver', 'gems', 'gold', 'gems')
> types <- factor(chests)

> print(types)
[1] gold   silver gems   gold   gems
Levels: gems gold silver

> as.integer(types)
[1] 2 3 1 2 1

> levels(types)
[1] "gems"   "gold"   "silver"

```

<br>
The following example takes the types variable and displays the points on the plot differently (triangle, square, circle) according to the type they're in with the help of `pch=as.integer(types)`:
```R
> chests <- c('gold', 'silver', 'gems', 'gold', 'gems')
> types <- factor(chests)
> weights <- c(300, 200, 100, 250, 150)
> prices <- c(9000, 5000, 12000, 7500, 18000)

> plot(weights, prices, pch=as.integer(types)) #in R
> qplot(weights, prices, color = types) #in ggplot

> legend("topright", levels(types), pch=1:length(levels(types))) #adds a legend
```

###Dataframes

You can think of a data frame as something akin to a database table or an Excel spreadsheet. It has a specific number of columns, each of which is expected to contain values of a particular type. It also has an indeterminate number of rows - sets of related values for each column.

```R
#bind variables to a dataframe:
> treasure <- data.frame(weights, prices, types)

#access one column of the dataframe:
> treasure$prices
[1]  9000  5000 12000  7500 18000

#read a file as a dataframe:
> read.csv("targets.csv")
```

<br>
###Example Workflow
```R
#Merging two dataframes.
#By default, it joins the frames on columns with the same name:
> piracy <- read.csv("piracy.csv")
> gdp <- read.table("gdp.txt", sep="  ", header=TRUE)
> countries <- merge(x = gdp, y = piracy)

#Plotting GDP against Piracy rate:
> plot(countries$GDP, countries$Piracy)

#Finding correlation coefficient:
> cor.test(countries$GDP, countries$Piracy)
-0.8203183

#Calculating the linear model for piracy rate by GDP
#Assign it to the line variable & draw it:
> line <- lm(countries$Piracy ~ countries$GDP)
> abline(line)

```
<br>
####Helpful
```R
#show how often an element occurs
> table(d$cat_short)
        bks   blg  isch   nws  shop   vid   web
 8170    35    40  6214   111     8    25 33832

# Barplot this table
> barplot(table(mtcars$cyl))
```
