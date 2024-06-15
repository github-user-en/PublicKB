**References:** 
- [Exploring Metadata in Scientific Images](https://www.youtube.com/watch?v=A4po9z61TME).


# JPEG/JPG Metadata
JPG image metadata standard is called  Exif (Exchangeable image file format).
The Exif header stores basic metadata like date, camera settings, and location in.

Japan Electronics and Information Technology Industries Association (JEITA) produced the initial definition of Exif standard. Today, JEITA along with Camera & Imaging Products Association (CIPA) defines and maintains the Exif standard to ensure compatibility and uniformity in metadata across 
various devices and software that handle digital images.


# DICOM Metadata
DICOM metadata includes: 
- image size, 
- image dimensions, 
- bit depth, 
- modality used to create the data, 
- patient information, 
- image position data, 
- etc.

DICOM (Digital Imaging and Communications in Medicine) is the international standard for medical images. DICOM metadata standards were originally defined by the American College of Radiology (ACR) and the National Electrical Manufacturers  Association (NEMA) in 1983 by forming a joint committee. Today, the DICOM Standard is managed by the Medical Imaging & Technology Alliance - a division of NEMA.

pip install pydicom
https://github.com/pydicom/pydicom

Sample DICOM images: 
https://www.rubomedical.com/dicom_files/

Accessing metadata using DICOM metadata tags:
https://www.dicomlibrary.com/dicom/dicom-tags/


# TIFF Metadata
The TIFF format was initially introduced by Aldus Corporation, and the first version, TIFF 1.0, was released in 1986. Adobe Systems later became involved in the development and standardization of TIFF. Today, Adobe holds the copyright on the TIFF specification. 

TIFF uses a structured format called the **Image File Directory (IFD)** to store metadata information. The IFD contains tags that define various metadata fields such as: 
- image dimensions, 
- color space, 
- compression method, 
- etc. 
Each tag in the IFD has a unique identifier (TagID) and is associated with a specific metadata field. The raw data for each tag is stored in the TIFF file along with its TagType, Count, and Offset. 

pip install tifffile

Useful resources:
- [TIFF Tags](https://www.loc.gov/preservation/digital/formats/content/tiff_tags.shtml)


# GeoTIFF Metadata
GeoTIFF is an extension of the TIFF file format that adds geospatial metadata  to the image. It allows for the storage of geographic information along with the raster data. 
- **Raster Data** = The usual pixel data in 2D images (or, in 2D multichannel images)

The GeoTIFF standard is maintained by the Open Geospatial Consortium (OGC)

The metadata in GeoTIFF is stored in the form of tags within the TIFF file (just like the regular TIFF file metadata). 

Download and install **GDAL** and **rasterio** first
pip install GDAL
pip install rasterio

| If pip install doesn't work, download the wheel for windows from here:                                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ~~ https://www.lfd.uci.edu/~gohlke/pythonlibs/#gdal ~~<br>~~ https://www.lfd.uci.edu/~gohlke/pythonlibs/#rasterio ~~<br>Since this link no longer works, you should look for the windows wheels at either of the following:<br>https://www.cgohlke.com/<br>https://github.com/cgohlke/geospatial-wheels/?tab=readme-ov-file |


# OME-TIFF Metadata
OME-TIFF is an extension of the TIFF file format for microscopy images and is part of the broader Open Microscopy Environment (OME) initiative. 

OME-TIFF = Open Microscopy Environment - Tagged Image File Format 

OME-TIFF stores multidimensional microscopy data and associated metadata. OME-TIFF stores metadata in a structured way using XML embedded within the TIFF file. The XML contains information about the microscope settings, acquisition parameters, and other meatadata. 

The metadata in OME-TIFF sticks to the [OME Data Model](https://docs.openmicroscopy.org/ome-model/6.0.1/), which defines a standard way of representing microscopy-related information. OME Consortium is responsible for the development and maintenance of the OME-TIFF standard.

In python, ometiff files can be read using tifffile library and metadata extracted the same way as above, like in regular tiff. But, let us use apeer_ometiff_library to extract the embedded xml metadata file.

pip install apeer-ometiff-library 

The Image read using this library would be a 5D array (see [this portion](https://youtu.be/A4po9z61TME?feature=shared&t=1974) of the video for more on these 5 dimensions)
