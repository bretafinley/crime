
# Crime

## Included Files
* data/ - Directory containing various data files. "test.csv" is a cut down file
	that I've been using for most tests.
* docs/ - Documentation directory which contains the project report, user manual,
	as well as Power Point presentation.
* images/ - Directory containing images for the MarkerCluster library for Google
	Maps.
* lib/ - Directory that contains library scripts and style sheets for the project.
	I use a number of third party software packages and they all can be found
	here.
* node_modules/ - This directory is created when the user runs the "npm install"
	command in order to initialize the project. This directory contans pertinent
	node software modules which the server uses in order to operate.
* .gitignore - Ignore file for GitHub, which I've been using for source control.
* app.js - Angular module declaration file. The project became too unwieldly to
	house in a single script, AngularJS became necessary in orer to better
	modularize my project.
* barchart.html - Template file for the barchart view of the visualization.
* bargraph.js - This JavaScript file provides the programming logic for the
	bargraph. This includes D3 code as well as data aggregation when the
	over-arching dataset changes.
* controller.js - Main controller file. This is the only controller in the
	application, most logic can be found here.
* heatmap.html - Template file for the heatmap view of the visualization.
* heatmap.js - This JavaScript file contains the programming logic for the
	heatmap. This includes D3 code as well as data aggregation when the
	over-arching dataset changes.
* index.html - This is the main HTML file for executing the application. This
	contains all of the relevant markup for the project and contains some
	Angular templating
* index.js - Server file. This contains all of the NodeJS code for executing the
	backend, as well as serving HTML files and crime data.
* package.json - Node project dependency file which keeps track of all of the node
	packages which this applicaiton uses. The command "node install" will need
	to be run in order to install these packages prior to execution.
* README - This readme documentation file.
* services.js - Angular services module. This file contains reusable library code
	for the rest of the project. Things like data access and date formatting are
	done here.

## Running
This project requires an installation of NodeJS on the server machine. NodeJS
comes with the Node Package Manager which can be used to install relevant
packages needed to run the application. Node can be downloaded at the following
url: https://nodejs.org/en/. Once Node has been downloaded and installed on the
server machine, the command "npm" should be available to you. Simply change into
the top level directory (which contains the package.json file) and run the
command "npm install". This will look at the dependencies required by the
project and downloaded and install them locally. Once the packages have been
installed, to run the server program, simply run "node index.js" from the same
directory. This will execute the server script and start an HTTP server running
on port 3000, or whichever port has been specified within the server script.
Simply browse to http://localhost:3000/ to view the running application.

## Data
The data being visualized is a collection of reported crimes occuring within the
city of Chicago, Illinois. These records have been sampled between January 1,
2001, and November 1, 2016. These records contain a variety of dimensions.

* ID - Unique identifier for the case.
* Case Number - Incremental numberic value representing that particular case.
* Date - Datetime on which the crime was reported.
* Block - City block on which the crime was reported.
* IUCR - Illinois Uniformed Crime Reporting number used to classify crimes.
* Primary Type - Category denoting the kind of criminal activity.
* Location Description - Brief description of the location of the crime.
* Arrest - Boolean value for whether or not an arrest was made.
* Domestic - Boolean value for whether or not the crime was a domestic dispute.
* Beat - The police beat this crme occurred on.
* District - City district this crime occurred in.
* Ward - City Ward in which the crime occurred.
* Community Area - 1 of the 77 community areas of Chicago.
* FBI Code - Identifier for mapping between numbers and offense categories.
* Year - The calendar year in which the crime was reported.
* Updated On - Datetime on which the record was last updated.
* Latitude - Geographical latitude value where the crime was reported.
* Longitude - Geographical longitude value where the crime was reported.
* Location - Combination of latitude and longitude values.

## Project
This project consists of four main views with a filter bar that is used for
filtering the overall dataset. Data is loaded when the server is started, data
is then requested by the frontend and pushed to these views. Data is requested
via an HTTP GET method call which passes route parameters used to filter the
data. Users can filter by date range, as well as crime type and the community
area the crimes occurred in. The first view is a Google Maps window which
represents the crimes geographically. Crimes are clustered together to improve
map performance. Clicking on a cluster zooms closer to that cluster. There are
manual zoom controls, as well as a toggle button which switches the map between
stylized and sattelite map views. A stick figure control also allows the user to
drag and drop this control anywhere on the map. This will provide the user with
a street view of that particular location. The table view shows the points
visible in the current map window. Only 20 points are shown in the table, so the
user will have to press the "Load More" button to show more rows in the table. A
query bar appears above the table which allows users to search the table by
specific criteria. The lower left corner displays the heat map view which
displays crime density by the community they occurred in and the type of crime
that was committed. Hovering over one of the squares will display a textual
version of the data represented by that particular square. The adjacent bar
graph represents a slice of the data being represented by the heat map. In this
view, the y-axis represents the frequency of the particular crime, while the
x-axis shows the community area. Below this graph is a select box which allows
the user to select the particular type of crime which the graph represents. In
effect, the graph gives the user a different kind of representation of the same
data being shown on each row of the heat map.