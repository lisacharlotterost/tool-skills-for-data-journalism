# qgis

### Find a scale to fill countries in Choropleth maps

1. doubleclick on layer
2. go to "Style"
3. select "graduated" instead of "Single Symbol"
4. choose Column
5. click "Classify" and see what happens

http://lisacharlotterost.github.io/2014/12/14/Styling-Choropleth-Maps-2/


**Equal Interval** - As the name suggests, this method will will create classes which are at the same size. If our data ranges from 0-100 and we want 10 classes, this method would create a class from 0-10, 10-20, 20-30 and so on - keeping each class the same size of 10 units.

**Quantile** - This method will decide the classes such that number of values in each class are the same. If there are 100 values and we want 4 classes, quantile method will decide the classes such that each class will have 25 values.

**Natural Breaks (Jenks)**- This algorithm tries to find natural groupings of data to create classes. The resulting classes will be such that there will be maximum variance between individual classes and least variance within each class.

**Standard Deviation**- This method will calculate the mean of the data, and create classes based on standard eviation from the mean.

**Pretty Breaks** - This is based on the statistical package R’s pretty algorithm. It is a bit complex, but the ‘pretty’ in the name means it creates class boundaries that are round numbers.
