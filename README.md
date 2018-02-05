# databc_gisserver_tips
These examples are provided for the following layers:
1. WSA - STREAM CENTRELINE NETWORK (50,000):
https://catalogue.data.gov.bc.ca/dataset/wsa-stream-centreline-network-50-000
2. Known BC Fish Observations and BC Fish Distributions
https://catalogue.data.gov.bc.ca/dataset/known-bc-fish-observations-and-bc-fish-distributions
The target area used in this demo is Whistler Creek, WBODY_ID=264722.

# WFS Requests
Unlike WMS requests, Web Feature Service requests return the actual geometry and full layer attributes, instead of just representing the data as an image tile. Although WFS requests are ultimately more ideal they can take much longer to process and can be impossibly slow or unavailable for larger regions.
[GeoServer](http://docs.geoserver.org/stable/en/user/services/wfs/reference.html)|[QGIS](https://docs.qgis.org/2.18/en/docs/training_manual/online_resources/wfs.html)|[Filter by attribute example](https://www.linz.govt.nz/data/linz-data-service/guides-and-documentation/wfs-filtering-by-attribute-or-feature)
## Describe Feature Type
Used to get field attribute information for a target layer (ie what's available). Field information request. Run the following URL.
```
https://openmaps.gov.bc.ca/geo/pub/WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP/ows?&service=WFS&request=DescribeFeatureType&version=2.0.0&typeNames=pub:WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP&outputformat=application/json&PROPERTYNAME=SPECIES_CODE&CQL_FILTER=WBODY_ID=264722
```
## Get Feature		
Gets all attributes and geometry & outputs as geojson. Easy, but slow. Requests more information from server than we need. Example below: Requests all FISS information for waterbody ID 264722 (Whistler Creek). Includes all geometry add additional attributes. Works, but poorly optimized. Notice the CQL filter applied.
```
https://openmaps.gov.bc.ca/geo/pub/WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP/ows?&service=WFS&request=GetFeature&version=2.0.0&typeNames=pub:WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP&outputformat=application/json&CQL_FILTER=WBODY_ID=264722
```
