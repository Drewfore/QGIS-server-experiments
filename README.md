# QGIS-server-experiments
In this repo are two html pages that consume a QGIS Server webservice showing some example applications using QGIS Server.
- Search.html: Is an example page that uses a layer from QGIS Server in a WFS capacity for an autocomplete search, once a searched record is selected it presents the features attributes to the user. Potential use cases for this type of service are POI style searches, and general enquiry of POIs for public consumption.
- Map.html: Is an example leaflet map that shows you can consume the layers from QGIS Server to create web maps and simple map embeds. While this example is basic it can be expanded upon to display multiple layers, layer controls, get feature info and more.

## Preqs - What do I need to use these pages?
You will need a QGIS Server running locally. Fortunately, this is now well documented and this example will be based on a windows install. If you are using a different OS, please follow the instructions for installing QGIS Server on your platform. Install guide listed below.

### QGIS Server install
Follow the steps documented here - https://docs.qgis.org/3.40/en/docs/server_manual/getting_started.html#installation-on-windows

When you get to "Step 4." which involves making changes to the httpd.conf file. I found that I didn't have to do all of these but there were two that were required to get me moving.

1. Change ```ScriptAlias /cgi-bin/ "${SRVROOT}/cgi-bin/"``` to ```ScriptAlias /cgi-bin/ "C:/OSGeo4W/apps/qgis/bin/"```
Note: when updating this path if you are using qgis-ltr then the path will need to be ```C:/OSGeo4W/apps/qgis-ltr/bin/```
2. At the bottom of the file add a reference to your project file
```SetEnv QGIS_PROJECT_FILE "C:/Users/*Your USERNAME*/lg_meetup/nsw_lga.qgz"``` 

With those steps completed youe would be able to load http://localhost and get a page that reads "It Works" or load the following page "http://localhost/cgi-bin/qgis_mapserv.fcgi.exe?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities" and get the XML get capabilities document for your map file.
