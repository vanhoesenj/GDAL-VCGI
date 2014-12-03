# **Overview of GDAL via a GUI**

This is a companion site to a VCGI webinar scheduled for December 16, 2014 titled "Afraid of GDAL, There's a GUI For That: Raster Mastering in QGIS."

## **Ok, we need some data!**

1. Start by visiting the [Shangri-La](http://vcgi.vermont.gov/opendata) of data clearinghouses to obtain a 30-meter DEM of Vermont (yes, yes I know there is a 10-meter version and LiDAR is available but time is precious and some people are using Comcast...). Enter 30 in the search dialog and download the *ElevationDEM_DEM24* layer.
2. We also need to download a vector layer from VCGI to demonstrate the full power of the GDAL library. You will also want to search for towns and download the *BoundaryTown_TWNBNDS* layer.
3. And lastly visit [LibreMap](http://libremap.org/data/state/vermont/) and search for Mansfield to get a DRG. This is a wonderful source for DRGs throughout the U.S.
4. 

## **TOP TEN GDAL TOOLS (no particular oder)**
  
#### **1. Extract Projection** ([gdalsrsinfo](http://gdal.org/1.11/gdalsrsinfo.html))
Useful for identifying projection within command line but less useful within a GUI-based GIS because you can typically view layer properties to find the same information. However in earlier versions of QGIS this was a useful tool when working with unfamiliar data sources.
#### **2. Warp Raster** ([gdalwarp](http://gdal.org/1.11/gdalwarp.html))
Similar to the Project Raster tool in the ArcGIS suite, this tool allows users to assign raster layers different spatial reference system (SRS).
#### **3. Assign Projection** (-a_srs)
Similar to the Define Projection tool in the ArcGIS suite, this option allows gdalwarp and gdal_translate to assign or change the layer SRS. 
#### **4. Translate** ([gdal_translate](http://gdal.org/1.11/gdal_translate.html))
This is the Leatherman (I mean not all Swiss Army knives are actually multitools right?) of the GDAL library. This tool allows us to change the raster output format (i.e. - JPG, GeoTiff, etc), create a subset of the layer (i.e. - crop <-- seriously, crop not clip...), change the output size (outsize), extract and mask individual bands (-b band, mask band), and variety of other options described in the documentation.
#### **5. DEM Tools** ([gdal_dem](http://www.gdal.org/gdaldem.html))
#### **6. Polygonize** ([gdal_polygonize.py](http://www.gdal.org/gdal_polygonize.html))
#### **7. Grid** ([gdal_grid](http://www.gdal.org/gdal_grid.html))
#### **8. Merge** ([gdal_merge.py](http://www.gdal.org/gdal_merge.html))
#### **9. Contour** ([gdal_contour](http://www.gdal.org/gdal_contour.html))
#### **10. Build Pyramids** ([gdaladdo](http://www.gdal.org/gdaladdo.html))