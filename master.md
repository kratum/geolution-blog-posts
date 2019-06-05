## LIDAR Data from OpenNRW

#### We will download and prepare LIDAR Data from opengeodata.nrw.de for further use in pdal and CloudCompare

What do we need:
- https://pdal.io/ - One very easy way to get pdal up and running on your system is by using the package manager [Anaconda](https://www.anaconda.com/).

Go to [opengeodata.nrw.de](https://www.opengeodata.nrw.de/produkte/geobasis/dom/dom1l/), select your desired dataset and download it. Inside  your downloaded zip file is a bunch of .xyz ascii files named like this:
- dom1l-fp_32353_5658_1_nw.xyz

> __dom1l__ is a german shortname for  _digitales Oberflächenmodell_ and that is like a DSM. Just for the sake of completeness. A DTM in english is a DGM in german.
__\_fp\___ is for _first pulse_ and __\_aw\___ for  water bodies
__\_#####_####\___ are the coordinates of the lower left corner of a sqkm in EPSG:25832

To use the data in 





[further information](https://rapidlasso.com/2017/01/03/first-open-lidar-in-germany/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEyNzMyNTM1MywtMTMyNzE1NzAzNSwtMT
kyNzM3NzUwOCwxMzQ5MjU1ODA2LDE2ODI3NzcyMTIsLTQ3OTAw
OTYwXX0=
-->