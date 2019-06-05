
## LIDAR Data from OpenNRW

#### We will download and prepare LIDAR Data from opengeodata.nrw.de for further use in pdal and CloudCompare
___

What do we need:
- https://pdal.io/ - One very easy way to get pdal up and running on your system is by using the package manager [Anaconda](https://www.anaconda.com/).

Go to [opengeodata.nrw.de](https://www.opengeodata.nrw.de/produkte/geobasis/dom/dom1l/), select your desired dataset and download it. Inside  your downloaded zip file is a bunch of .xyz ascii files named like this:
- dom1l-fp_32353_5658_1_nw.xyz

> __dom1l__ is a german shortname for  _digitales Oberflächenmodell_ and that is like a DSM. Just for the sake of completeness. A DTM in english is a DGM in german.
__\_fp\___ is for _first pulse_ and __\_aw\___ for  water bodies
__\_#####_####\___ are the coordinates of the lower left corner of a sqkm in EPSG:25832
[Here](https://github.com/kratum/geolution-blog-posts/blob/master/gitter_25832_1km_nrw.geojson) you can download a file with the sqkm grid for NRW, DE with some metadata from [openNRW](https://www.opengeodata.nrw.de/produkte/geobasis/dom/dom1l/dom1l_meta.zip)
___
Some preprocessing is necessary befor we can start du use the data. We will compress the data to .laz format, remove outliers and set a spatial reference. Here comes pdal into play. The concept of pdal is to build pipelines for point cloud processing like filtering, classification or transformation. Those pipelines are simple .json files. Go to [pdal.io](https://pdal.io/) to get more information about how pdal works.

example pipeline:
```json
{
    "pipeline":[
        {
            "type":"readers.text",
            "filename":"dom1l-fp_32358_5655_1_nw.xyz",
            "header":"x,y,z",
            "spatialreference":"EPSG:25832"
        },
	{
	    "type":"filters.outlier",
	    "method":"statistical",
	    "mean_k":12,
	    "multiplier":2.2
	},
        {
            "type":"writers.las",
            "filename":"dom1l-fp_32358_5655_1_nw.laz",
            "a_srs":"EPSG:25832"
        }
    ]
}
```
This pipeline can be used with
```
pdal pipeline <PATH_TO_PIPELINE> 
```
and it will read the xyz file, detect outliers and write a compressed las file with a spatial reference.



[further information](https://rapidlasso.com/2017/01/03/first-open-lidar-in-germany/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQ5ODg5NTM3LDEyMzA0OTExMDRdfQ==
-->