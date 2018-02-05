# databc_gisserver_tips
WMS and WFS Request tips for Data BC server

# WFS Requests
Unlike WMS requests, Web Feature Service requests return the actual geometry and full layer attributes, instead of just representing the data as an image tile. Although WFS requests are ultimately more ideal they can take much longer to process and can be impossibly slow or unavailable for larger regions.

[QGIS](https://docs.qgis.org/2.18/en/docs/training_manual/online_resources/wfs.html)|

		Info Request
		https://openmaps.gov.bc.ca/geo/pub/WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP/ows?&service=WFS&request=DescribeFeatureType&version=2.0.0&typeNames=pub:WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP&outputformat=application/json&PROPERTYNAME=SPECIES_CODE&CQL_FILTER=WBODY_ID=264722
		
		
		Working For Target Waterbody ID
		
//===========================================
// Get all features with simple filter 
//===========================================
// Gets all attributes and geometry & outputs as geojson.
// Easy, but slow. Requests more information from user than we need.
// Example below: Requests all FISS information for waterbody ID 264722 (Whistler Creek)
// Includes all geometry add additional attributes.

		https://openmaps.gov.bc.ca/geo/pub/WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP/ows?&
		service=WFS&
		request=GetFeature&
		version=2.0.0&
		typeNames=pub:WHSE_FISH.FISS_FISH_OBSRVTN_PNT_SP&
		outputformat=application/json&
		CQL_FILTER=WBODY_ID=264722
