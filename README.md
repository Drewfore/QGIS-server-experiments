# QGIS-server-experiments
In this repo are two html pages that consume a QGIS Server webservice showing some example applications using QGIS Server.
- Search.html: Is an example page that uses a layer from QGIS Server in a WFS capacity for an autocomplete search, once a searched record is selected it presents the features attributes to the user. Potential use cases for this type of service are POI style searches, and general enquiry of POIs for public consumption.
- Map.html: Is an example leaflet map that shows you can consume the layers from QGIS Server to create web maps and simple map embeds. While this example is basic it can be expanded upon to display multiple layers, layer controls, get feature info and more.

## Preqs - What do I need to use these pages?
You will need a QGIS Server running locally. Fortunately, this is now well documented and this example will be based on a windows install. If you are using a different OS, please follow the instructions for installing QGIS Server on your platform. Install guide listed below.

### QGIS Server install
Follow the steps documented here - https://docs.qgis.org/3.40/en/docs/server_manual/getting_started.html#installation-on-windows

When you get to "Step 4." you should only need to change two items in the ```C:\OSGeo4w\apps\apache\conf\httpd.conf``` file. These are:
- 1 ```ScriptAlias /cgi-bin/ "${SRVROOT}/cgi-bin/"``` to ```ScriptAlias /cgi-bin/ "C:/OSGeo4W/apps/qgis/bin/"```
- 2 At the bottom of the file add a reference to your project file ```# default QGIS project
SetEnv QGIS_PROJECT_FILE "C:/Users/*Your USERNAME*/qgis_projects/qgis-server-tutorial-data/world.qgs"``` 
