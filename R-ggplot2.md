# R: ggplot2

Cheatsheet: https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf


### Facet_wrap, aka What do tildes in ggplot do?
```R
myFormula <- Species ~ Sepal.Length + Petal.Length
# means: "Species depends on Sepal Length and Petal Length

facet_wrap( ~ death )
# means: "All the defined things beforehand in ggplot, depending on the death variable"

facet_grid(. ~ death) # facet into columns
facet_grid(year ~ .) # facet into rows
facet_grid(year ~ deaths) #facet into rows and columns
```


### Density charts and Histograms
```R 
# plot histogram
ggplot(d,aes(x=yeah)) + 
  geom_histogram()
  
# plot mini density small multiples and median line for each state
ggplot(d,aes(x=yeah)) + 
  geom_density() + 
  facet_wrap(~death) + ylim(0,0.25)
  
# with ggVis
d %>%
  ggvis(~yeah) %>%
  layer_histograms(width= input_slider(1, 50, step = 5))
```


# This removes all legends
bp + theme(legend.position="none")