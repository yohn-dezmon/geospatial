https://advena.hashnode.dev/heavy-map-visualizations-fundamentals-for-web-developers

# Frontend Geospatial Overview

# Vector Shapes:

- points (lat, lon)
- lines + polylines (connected points, connected lines)
- polygons (shapes, points that form a shape)

# 2.1 Base Maps

- every geospatial app starts with a base map
  Services that offer base maps:
- OpenStreeMap (OSM)
- Google Maps
- Mapbox

You can draw vector shapes on top of satellite images and label them with meaningful info.

- this is how a basemap is created! (you need to do this for all features, roads, forests, etc.)

# 2.2 Your Geospatial Data

- you take a basemap, and then add additional geospatial data. This makes your application UNIQUE!
- you can store geospatial data in GeoJSON
  - GeoJSON is simply a JSON format that follows a specific structure for geospatial data.
    This represents a bus station

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        // Coordinates are stored in [longitude, latitude] order
        "coordinates": [-73.983, 40.761]
      },
      "properties": {
        "station_id": "12345",
        "handicap_friendly": false
      }
    },
    ...
  ]
}
```

Shapefiles:

- legacy, outdated, but used by GIS programs like QGIS
- .shp

GeoPackage

- .gpkg
- more efficient for queries

GeoJSON:

- can result in really large files > 100 MB
- managing this efficiently for frontends is key!!
- it's easy to work with but not the best for storing or serving large datasets

# 2.3 Serving Geospatial Data

- you can serve GeoJSON from your backend
- you can serve it from S3, Backblaze B2, or GCS
- sometimes you can use PostgreSQL with PostGIS, or you can use Mapbox as a hosting service (more complex usecases)
- you can also store data in Parquet (!!!!) -- which is an alternative to Shapefile (and way more efficient!)

# 2.4 Putting things together

- you can use JavaScript libraries to add markers, routes, and shapes to the basemap (!)
- some JS libraries just render basemaps, while others support editing it

# 3.1 JS Map Libraries

- some will constrict you to a specific basemap
- certain basemaps have higher costs for their API (e.g. google)
- Google Maps JS API
  -
- Mapbox GL JS
  - offers a generous free tier
