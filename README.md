# Leaflet-Solr-Heatmap

A Leaflet plugin that visualizes heatmap facets from Solr 5.x

## Using with Leaflet

```javascript
// Create a SolrHeatmap layer and add it to the map
var solr = L.solrHeatmap('http://127.0.0.1:8983/solr/gettingstarted', {
  // Solr field with geospatial data (should be type Spatial Recursive Prefix Tree)
  field: 'loc_srpt',

  // Set type of visualization. Allowed types: 'geojsonGrid', 'clusters'
  // Note: 'clusters' requires LeafletMarkerClusterer
  type: 'geojsonGrid'
}).addTo(map);
```

Option | Type | Default | Description
------ | ---- | ------- | -----------
`field` | `String` | `null` | *Required.* Solr field with geospatial data (should be type Spatial Recursive Prefix Tree)
`type` | `String` | `'geojsonGrid'` | Type of visualization. Accepts `geojsonGrid`, `clusters` and `heatmap`
`solrRequestHandler` | `String` | `'select'` | Request handler for Solr
`colors` | `Array` | `['#f1eef6', '#d7b5d8', '#df65b0', '#dd1c77', '#980043']` | Colors for heatmap.  Array can be of any length.
`maxSampleSize` | `Number` | `Number.MAX_SAFE_INTEGER` | For improved performance, run Jenks classification on only a sample of Solr counts.  Default value turns off sampling.  Typical value is 400.

### Events

`L.SolrHeatmap` layers fire all of the typical events from Leaflet. Additional events include:

Event | Data | Description
----- | ---- | -----------
`dataAdded` | `Object` | fires when data is added to the map. Returns an object which is the JSON response from the Solr server

## Running locally

Install Dependencies
```sh
# Install JavaScript depencencies
$ npm install

# Install local solr
$ gem install solr_wrapper
```

Run Solr
```sh
$ solr_wrapper
```

Index fixture data
```sh
$ npm run index
```

Start local server
```sh
npm run start
```

View the example at [http://127.0.0.1:8000/example/](http://127.0.0.1:8000/example/)
