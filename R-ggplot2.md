# R: ggplot2

Cheatsheet: https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf


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
