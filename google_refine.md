# Open Refine


## Best Tricks

- ```value.replace("+", "").replace(",","")``` turns "45,303+" into "45303"
- ```value.split(" ").reverse().join(", ")``` turns "Paul Smith" into "Smith, Paul"
- ```value.replace(/./,'a')``` turns "heute89ah//" into "aaaaaaaaaaa"
- ```value.replace(/.+/,'a')``` turns "heute89ah//" into "a"
- ```value.replace(/\w/,'a')``` turns "heute89ah//" into "aaaaaaaaa//"
- Text Facet -> Cluster
- Get Geo-Coordinates out of Streetnames and postcodes directly in Refine (AWESOME): http://enipedia.tudelft.nl/wiki/OpenRefine_Tutorial#Geocoding_names_and_addresses


## Regular expressions
(more here: http://www.cleo.com/support/byproduct/lexicom/usersguide/using_wildcards_and_regular_expressions.htm)

- ```\d```, a digit `([0-9])`
- ```\D```, a non-digit `([^0-9])`
- ```\w```, a word (alphanumeric) `([a-zA-Z0-9])`
- ```\W```, a non-word `([^a-zA-Z0-9])`
- ```\s```, a whitespace `([ \t\n\r\f])`
- ```\S```, a non-whitespace `([^ \t\n\r\f])`


## Tutorials

- One big example, with geocoding and deduplicating: http://enipedia.tudelft.nl/wiki/OpenRefine_Tutorial#Geocoding_names_and_addresses
- Whole documentation: https://github.com/OpenRefine/OpenRefine/wiki/Documentation-For-Users
- 3 Intro Screencasts: https://github.com/OpenRefine/OpenRefine/wiki/Screencasts
