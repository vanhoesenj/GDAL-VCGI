# **Overview of GDAL via a GUI**

This is a companion site to a VCGI webinar scheduled for December 16, 2014 titled "Afraid of GDAL, There's a GUI For That: Raster Mastering in QGIS." The primary goal of this presentation is to demonstrate a GUI-based means of accessing the powerful tools available in the GDAL library. If you weren't scarred by command line DOS or PC ArcINFO you might be more inclined to access these tools (or at least ones you might use regularly) via command line given that processing time is often [reduced.](http://gis.amherstma.gov/data/springnearc2013/Session3/MapServices/NEARC_ASimmons_5_14_13.pdf) So if you wanted to convert between raster formats, you could simply fire up a command line terminal and enter:

 `gdal_translate -of "GTiff" ~path/input_grid.jpg ~path/output_grid.tif`

However if your response to that syntax is:

![](http://media.giphy.com/media/IJjcaynRaNBWE/giphy.gif)

don't worry - that's the point of the webinar and this brief tutorial.

***
# **Ok, we need to procure some data!**

1. Start by visiting the [Shangri-La](http://vcgi.vermont.gov/opendata) of data clearinghouses to obtain a 30-meter DEM of Vermont (yes, yes I know there is a 10-meter version and LiDAR is available but time is precious and some people are using Comcast...). Enter 30 in the search dialog and download the *ElevationDEM_DEM24* layer.
2. We also need to download a vector layer from VCGI to demonstrate the full power of the GDAL library. You will also want to search for towns and download the *BoundaryTown_TWNBNDS* layer.
3. And lastly visit [LibreMap](http://libremap.org/data/state/vermont/) and search for Mansfield to get a DRG. This is a wonderful source for DRGs throughout the U.S.
4. You could also [download](http://www.anr.state.vt.us/dec/geo/StateBedrockMap2012.htm) the bedrock geologic map of Vermont. For no particular reason other than it's gorgeous (and really informative I might add). Enjoy it.

![](https://raw.githubusercontent.com/vanhoesenj/GDAL-VCGI/master/Images/geology.png)

****
## **TOP TEN GDAL TOOLS (no particular order)**
  
##### **1. Extract Projection** ([gdalsrsinfo](http://gdal.org/1.11/gdalsrsinfo.html))
Useful for identifying projection within command line but less useful within a GUI-based GIS because you can typically view layer properties to find the same information. However in earlier versions of QGIS this was a useful tool when working with unfamiliar data sources.

##### **2. Warp Raster** ([gdalwarp](http://gdal.org/1.11/gdalwarp.html))
Similar to the Project Raster tool in the ESRI ArcGIS suite, this tool primarily allows users to assign raster layers different spatial reference system (SRS). However there are numerous options described in the documentation. One useful option is the `-r resampling_method` when up sampling or downsampling data. But this utility allows the user to also pass many other optional variables such as output format and nodata masking values (i.e. `-of format` and `-srcnodata`).

##### **3. Assign Projection** (`-a_srs`)
Similar to the Define Projection tool in the ESRI ArcGIS suite, this is another optional parameter that allows gdalwarp and gdal_translate to assign or change the layer SRS. Similar to the [Define Projection](https://www.flickr.com/photos/43782063@N07/14869020514/sizes/o/) tool it is important to make sure this tool isn't used in lieu of `gdalwarp`, meaning it is important to avoid assigning an SRS rather than re-projecting the data (i.e. - just 'telling' the data it is in an SRS that it is not...).

##### **4. Translate** ([gdal_translate](http://gdal.org/1.11/gdal_translate.html))
This is the Leatherman (I mean not all Swiss Army knives are actually multitools right?) of the GDAL library. This tool allows us to change the raster output format (i.e. - JPG, GeoTiff, etc), create a subset of the layer (i.e. - crop <-- seriously, crop not clip...), change the output size (outsize), extract and mask individual bands (`-b band`, `mask band`), and variety of other options described in the documentation.

##### **5. DEM Tools** ([gdal_dem](http://www.gdal.org/gdaldem.html))
This utility provides many of the most commonly used functions available through ESRI's Spatial Analyst extension for creating derivative layers from digital elevation models (i.e. - hillshade, slope, aspect, ruggedness index, etc). An additional useful option is the color-relief syntax, which allows the user to pass a color rule set specifying which colors should be assigned to different elevation ranges. Just to reiterate the point about the processing time between command line via a GUI, this function can be accessed using the following syntax: 

`gdaldem color-relief input_grid.tif color-rules.txt output-color-relief.tif`).
 
##### **6. Polygonize** ([gdal_polygonize.py](http://www.gdal.org/gdal_polygonize.html))
Although the majority of the tools in the GDAl library were developed for raster analysis/processing it is often useful to convert raster layers to polygon features for cartographic representation. This utility is similar to the Raster to Polygon tool available in the ESRI ArcMap suite.

##### **7. Grid** ([gdal_grid](http://www.gdal.org/gdal_grid.html))
It is often... updating soon.

##### **8. Merge** ([gdal_merge.py](http://www.gdal.org/gdal_merge.html))

##### **9. Contour** ([gdal_contour](http://www.gdal.org/gdal_contour.html))

##### **10. Build Pyramids** ([gdaladdo](http://www.gdal.org/gdaladdo.html))