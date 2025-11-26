# QGIS-server-experiments
Example web applications using QGIS Server backend

## What do we have here
In this repo are two html pages that consume a QGIS Server webservice showing some example applications of using QGIS Server.
- Search.html: Is an example page that uses a layer from QGIS Server in a WFS capacity for an autocomplete search, once a searched record is selected it presents the features attributes to the user. Potential use cases for this type of service are POI style searches, and general enquiry of POIs for public consumption.
- Map.html: Is an example leaflet map that shows you can consume the layers from QGIS Server to create web maps and simple map embeds. While this example is basic it can be expanded upon to display multiple layers, layer controls, get feature info and more.

## What do I need to use these pages?
You will need a QGIS Server running. Fortunately, this is now well documented in the QGIS Server docs https://docs.qgis.org/3.40/en/docs/server_manual/getting_started.html#installation-on-windows
