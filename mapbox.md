# Mapbox

open Tilemill:
cd Tilemill
node index.js


## Useful links:

- country borders as geo json: http://data.okfn.org/data/datasets/geo-boundaries-world-110m

- CartoCSS documentation: https://github.com/mapbox/carto/blob/master/docs/latest.md
- The original OSM design as CartoCSS https://github.com/gravitystorm/openstreetmap-carto
- A quiet design for OSM maps: https://github.com/datadesk/osm-quiet-la
- OSM City/Country data:
    - http://metro.teczno.com/#berlin OLD
    - https://mapzen.com/metro-extracts/
    - http://download.geofabrik.de/

- Erklärung, wie man aus PLZ + Straße in R die Koordinaten bekommt: http://www.de-egge.de/2013/10/oeffentliche-wlan-spots-in-berlin/ + anderes Tool dafür: https://www.drupal.org/project/geocoder
- Sort Data:http://www.qgis.org/de/site/
- ArgGIS: http://www.esri.com/
- Übersicht über alle Tools:
http://gis.stackexchange.com/questions/8032/how-do-various-javascript-mapping-libraries-compare

<br>


## CartoCSS - most basic styles

- duplicates the layer, in this case to insert an outline and inline

```css
#layer {
  ::outline {
    line-width: 6;
    line-color: black;
  }
  line-width: 2;
  line-color: white;
}
```

- styles every sub-type differently:

```css
#roads {
  [class='motorway'] {line-width: 4;}
  [class='main'] {line-width: 2;}
  [class='street'] {line-width: 1;}
}
```

- styles everything in a spcific zoom level:


```css
#layer[zoom>=4][zoom<=10] {line-width: 1;}
```
```css
#cities {
  [zoom>=4][population>1000000],
  [zoom>=5][population>500000],
  [zoom>=6][population>100000] {text-name: [name];}
}
```

- selects everything that is NOT a certain type:

```
#roads[class!='motorway'] {line-width: 1;}
```



## Tutorials I watched

- How to import and style a OSM Berlin map https://www.youtube.com/watch?v=BmYqxF8QgnA




## File formats

| Extension | Explanation |
| --- | --- |
| OSM | Open Street Map |
| Geo-JSON | 1:3 |
| .shp | Shapefile. Common standard for representing geospatial vector data (describes points, polygons and lines) |
| .pbf | 1:5 |
| .pbf | 1:5 |
| GTFS | 1:6 |
| GML | 1:6 |
| GPX | an XML schema designed as a common GPS data format  |
| WFS | 1:6 |
| GIS | Geographic Information System. Used when talking about "GIS Software" (http://en.wikipedia.org/wiki/List_of_geographic_information_systems_software) like ArgGIS or QGis| <br>
<br>
