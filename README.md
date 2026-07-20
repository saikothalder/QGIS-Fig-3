# QGIS-
Project re-open: Double click the "Final Project.qgz"
QGIS Mapping Workflow: 
Stage 1: Data Import & Pre-processing
*Load River Shapefile: Go to Browser > select shapefile and import the national waterway shapefile. Extract the four specific study rivers > Go to layer > save selected as features> select folder then save. 
*Reproject Layer (UTM 46N): Right-click the extracted river layer, select layer> vector > Data management tool > reproject layer > Change the CRS to EPSG:32646 - WGS 84 / UTM zone 46N to ensure accurate metric distance measurements.
*Apply Fixed Buffer: Go to Vector > Geoprocessing Tools > Buffer. Set the reprojected river layer as input, enter your fixed distance, and run it to create the defined river extent layer.
*Import Field Data: Go to Layer > Add Layer > Add Delimited Text Layer. Choose CSV file containing the sampling coordinates, tr, and u values. Set X field as Longitude and Y field as Latitude, then click Add to generate the point layer.
Stage 2: Spatial Interpolation & tr Visualization
*Run IDW Interpolation: Open the Processing Toolbox and search for IDW Interpolation.
1.	Vector Layer: Select sampling point layer.
2.	Interpolation Attribute: Select the recovery time (tr) column and click the "+" icon.
3.	Extent: Set it to match buffered river extent layer.
4.	Click Run to generate the tr raster surface.
*Style tr Raster: Right-click the new raster layer > Properties > Symbology.
1.	Change Render Type to Singleband Pseudocolor.
2.	Choose a Blue color ramp. Set Dark Blue for maximum values (High tr: Slow recovery) and Light Blue for minimum values (Low tr: Fast recovery).
Stage 3: Velocity (u) Point Overlay & Symbology
*Overlay Points: In the Layers Panel, drag the original sampling point layer to the very top so it sits over the newly created tr raster.
*Apply Graduated Style for Velocity: Right-click the point layer > Properties > Symbology.
1.	Change the top dropdown from Single Symbol to Graduated.
2.	Value: Select the velocity (u) column.
3.	Color Ramp: Choose a Red color ramp.
4.	Change Mode to Equal Interval or Quantile, then click Classify.
5.	Adjust the colors so that Dark Red dots represent low velocity and Light Red dots represent high velocity.
Stage 4: Spatial Comparison & Hotspot Mapping
*Visual Correlation: Turn on both the styled tr raster and the graduated velocity point layer simultaneously.
*Identify Hotspots: Scan the map visually to locate Pollution Hotspots-these are the exact geographic areas where a Dark Red dot (critically low velocity) sits directly on top of a Dark Blue raster zone (high oxygen recovery time, tr).
Stage 5: Map Print Layout
*Open New Print Layout: Go to the top menu and click Project > New Print Layout. Give it a name (e.g., "Fig.3") and click OK.
*Add Map to Canvas: In the layout window, click the Add Map icon (a small map page icon on the left toolbar) and click-and-drag over the blank canvas to display your QGIS map.
*Add Map Elements (Optional): Use the left toolbar to add essential map elements:
1.	Add Legend: Click Add Item > Add Legend to show the tr and velocity color scales.
2.	Add North Arrow & Scale Bar: Use Add North Arrow and Add Scale Bar to maintain geographic standards.
Stage 4: Export and Save:
*As Image (JPEG/PNG): Go to Layout > Export as Image. Choose folder, name the file, and set the resolution (1200 DPI) before clicking Save.

