# QGIS-server-experiments
This repo contains resources that were presented at a local government meetup in Mudgee 2/12/2025.
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

### Deploy the QGIS project
Take the "LG_Meetup" folder and place it into your ```C:/Users/*Your USERNAME*``` folder. This location should match the ```QGIS_PROJECT_FILE``` environment variable that you set in the step above.

### Deploy the pages
To see the example pages that I showed in the demo at Mudgee. Grab the two html pages from this repo and place them into the following folder "C:\OSGeo4W\apps\apache\htdocs"

<img width="642" height="246" alt="image" src="https://github.com/user-attachments/assets/da51a774-f022-499e-a916-bf06dae845b1" />

The htdocs folder is the publishing folder for Apache. The index.html file is the default page that contains the "It Works" message. Now with these two new HTML files in this folder we should be able to load the following URLS and get a page.
- http://localhost/search.html
- http://localhost/map.html


## QGIS Project
The QGIS project is a simple project containing two layers.

- 1 NSW local government areas with a grey single symbol renderer.
- 2 NSW local government areas with a categoriesed renderer based on LGA area.

<img width="1274" height="831" alt="image" src="https://github.com/user-attachments/assets/489e7b13-cbdf-43d6-8625-c737f855b9c5" />

## Search.html
The search page is an example web page which uses a WFS layer from a QGIS Server project.
This page uses the "localgovernmentarea" layer from the QGIS project. This layer is published as a WFS layer and the search input on this page uses that resource to provide the data for the autocomplete search. Once a record is selected from the search that feature is identified and all of the features attributes are presented to the user.

<img width="1044" height="425" alt="image" src="https://github.com/user-attachments/assets/d22f5abe-b991-4fc2-b45a-7298659ad741" />

## Map.html
The map page is an example of how you can request layers from the QGIS Server to be used in a web map library like Leaflet.
This is a simple web app that fetches the layers from the QGIS project and presents them to a layer list. A user can turn on/off a layer and see this represented on the map. They can also click on a feature to access the attribute information of the top most layer. This concept can be expanded to create a GIS Viewer.

<img width="1051" height="861" alt="image" src="https://github.com/user-attachments/assets/cfecfcf9-360d-4e86-a6d8-c417e5dc89b3" />

