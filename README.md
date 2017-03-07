# How to use *NLmaps* in Leaflet

See [the online demo](https://nlmaps.github.io/leaflet/leaflet_nlmaps.html).

## Prerequisites

* Include [Leaflet](http://leaflet.com) for plotting the map.

```html
<script src="https://unpkg.com/leaflet@1.0.3/dist/leaflet.js"></script>
```

* Include [Proj4Js](http://proj4js.org/) to map between different
  coordinate systems.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/proj4js/2.4.1/proj4.js"></script>
```

* Include [Proj4Leaflet](http://kartena.github.io/Proj4Leaflet/) to
  map coordinates used by *NLmaps* to coordinates used by Leaflet
  (WGS84):

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/proj4leaflet/1.0.1/proj4leaflet.min.js"></script>
```

## Map initialization

```js
L.map('nlmap', {
  zoom: 4,
  center: [ 52.2112,5.9699],
  layers: [
    new L.tileLayer.wms('http://geodata.nationaalgeoregister.nl/tms/1.0.0/brtachtergrondkaart/{z}/{x}/{y}.png', {tms: true})
  ],
  crs: new L.Proj.CRS("EPSG:28992", "+proj=sterea +lat_0=52.15616055555555 +lon_0=5.38763888888889 +k=0.9999079 +x_0=155000 +y_0=463000 +ellps=bessel +units=m +towgs84=565.2369,50.0087,465.658,-0.406857330322398,0.350732676542563,-1.8703473836068,4.0812 +no_defs", {
    transformation: new L.Transformation(1,285401.92,-1,903401.92),
    scales: [3440.64, 1720.32, 860.16, 430.08, 215.04, 107.52, 53.76, 26.88, 13.44, 6.72, 3.36, 1.68, 0.84, 0.42].map(function(res) {return 1/res}),
    bounds:new L.bounds([-285401.92, 22598.08], [595401.9199999999, 903401.9199999999]),
  }),
});
```

# Sites that already use *NLmaps*+Leaflet

  - [Kadaster Linked Data Platform](https://data.pdok.nl/yasgui#query=prefix+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0Aprefix+top%3A+%3Chttp%3A%2F%2Fbrt.basisregistraties.overheid.nl%2Fdef%2Ftop10nl%23%3E%0Aprefix+geo%3A+%3Chttp%3A%2F%2Fwww.opengis.net%2Font%2Fgeosparql%23%3E%0Aselect+%3Ffeature+%3FwktLiteral+%7B%0A++%3Ffeature+rdf%3Atype+top%3AHeemtuin+.%0A++%3Ffeature+geo%3AhasGeometry+%3Fgeometry+.%0A++%3Fgeometry+geo%3AasWKT+%3FwktLiteral+.%0A%7D%0Alimit+100%0A&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=%2Fsparql&requestMethod=POST&tabTitle=Query&headers=%7B%7D&outputFormat=leaflet) for visualizing SPARQL query results.

# How to use OpenStreetMaps in Leaflet

For comparison, this is how the installation for OpenStreetMaps works.

See [the online demo](https://nlmaps.github.io/leaflet/leaflet_openstreetmaps.html).


## Prerequisites

* [Leaflet](http://leaflet.com) for plotting the map:

```html
<script src="https://unpkg.com/leaflet@1.0.3/dist/leaflet.js"></script>
```

## Map initialization

```js
L.map('nlmap', {
  layers: [new L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png')],
  center: [ 52.2112,5.9699],
  zoom:9
});
```
