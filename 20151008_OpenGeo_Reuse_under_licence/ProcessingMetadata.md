# LUCAS OS Metadata summary

This notebook produces metadata to summarise the files provided by the Ordnance Survey.

The LUCAS project is establishing a research partnership with the Ordnance Survey (OS) for its sustainable cities research activities. This partnership will cover such areas as data and knowledge exchange. The LUCAS project is global in extent but has a UK focus on the city of Nottingham. The OS have provided the project with copies of AddressBase (Premium and Plus). Mastermap has been sourced from EDINA. 

During March 2015 the LUCAS team requested remote sensing data from the OS through Dr Isabel Sargent. The OS agreed to provide the following data for the Nottingham City region:

* Raw data
	* stereo multiband (R,G,B, NIR)
	* stereo panchromatic
* Derived
	* Orthorectified multiband (R,G,B, NIR) at 50cm pixel resolution
	* Orthorectified multiband (R,G,B, NIR) at 15cm pixel resolution 
	* Photograpmmetric Digital Surface Model (DSM) at 50cm pixel resolution
	
This data was delivered in late May 2015. This document describes the extraction of summary metadata and forms part of the feedback to Ordnance Survey.

## Data Summary

The data was provided on a USB drive and comprised of the following folders contained in a root *Nottingham* folder:

```
.
├── 4 Band stereo images
│   ├── NOTTINGHAM05_IZZY_001.tif
├── DSM 50cm
│   ├── SK5029-50cm.tif
├── Ortho 4 band non balanced 50cm
│   ├── SK5029-RGBI-50cm.tfw
│   ├── SK5029-RGBI-50cm.tif
├── Ortho panchromatic 15cm
│   ├── SK5029-RGB-15cm.tfw
│   ├── SK5029-RGB-15cm.tif
└── Pan stereo images
    ├── NOTTINGHAM05_IZZY_001.tif
```

Each image file was in a *.tif* (Tagged Image File Format). The derived data in the folders prefixed *Ortho* contained associated *.tfw* GeoTiff metadata files.

No sensor or flight metadata was provided.

The spatial extent of the data covered the full Nottingham area with a bounding box from LL - 450000,329000 to UR - 470000,310000 in EPSG 27700 projection.

The following potential issues were observed with these data:

* The *Ortho* panchromatic and multiband images did not contain projection information (easy to resolve we know what it is)
* The band order in the multiband imagery is unclear - from examining the metadata and the spectral profile we believe that band 1, 2, 3 and 4 correspond to Red, Green, Blue and Near Infra-red respectively (as opposed to a spectral ordering of B, G, R, NIR). Could this be confirmed?
* Sensor and flight metadata would improve the re-use and processing potential of the data (and would explicitly confirm the band ordering)
* The tiff files in the *4 Band stereo images* appear corrupt. They are whited out (very low dynamic range). These data are not critical but for completeness we would appreciate a new cut.


### Naming conventions

It was noted that there is a pattern to the naming convention for the processed files but it is not systematically applied. The name is broken up as follows (with a '-' separator):

*[OS 1km square/]*-*[bands?/type]*-*[ground resolution and units]*.*[file format extension]*

1. [OS 1km square] The Ordnance survey 1km square for the data 
1. [bands?/type] There is some ambiguity in what this represents. It's not filled in for the DSM, but it does not represent the bands (for example the four band multiband contains RGBI (Red, Green, Blue and Infra-red), however, the panchromatic (single band image) is donated as RGB (three bands). This leads me to assume this means crude spectral sensitivity. 
    * It would be nice to know that, for example, the file *SK5029-50cm.tif* refers to a DSM from the filename alone. 
1. [ground resolution and units] explicit for projected data

There was no naming convention for the raw data files.

## Pre processing

The following pre-processing was undertaken

### Folder Rationalisation

The supplied folders were renamed. All spaces were removed. The folders contained *raw* data were placed in a directory called *Raw*. The folders containing *derived data* were placed ina  direcotry called *Processed*.

This resulted in the following data structure:

```
├── Processed
│   ├── DSM_50cm
│   │   ├── SK5029-50cm.tif
│   ├── Ortho_4_band_non_balanced_50cm
│   │   ├── SK5029-RGBI-50cm.tfw
│   │   ├── SK5029-RGBI-50cm.tif
│   └── Ortho_panchromatic_15cm
│       ├── SK5029-RGB-15cm.tfw
│       ├── SK5029-RGB-15cm.tif
└── Raw
    ├── 4_Band_stereo_images
    │   ├── NOTTINGHAM05_IZZY_001.tif
    └── Pan_stereo_images
        ├── NOTTINGHAM05_IZZY_001.tif
```

These were all placed into a new *Data* folder.

## Metadata processing and summaries


Metadata summaries were generated solely for the processed data using the scripts below. These can be conceptually summarised as follows:


* Import required libraries
* Create new definitions
	* create_composite (create true and false colour composites)
	* create_composite_rescale  (create rescaled true and false colour composites)
	* plot_img_hist_and_imgEQ (plot image chips and histograms)
	* tif_image_output (output the tif images)
* generate project metadata and housekeeping
	* ensure files and directories exist
* Collate file and folder data in a Pandas dataframe
	* 'walk' over the files in the supplied 'root' directory (datadir)
	* create list of lists (fileList) of relativePath, filePrefix, fileSuffix
	* convert list into a dataFrame (df)
		* permanently sort frame so outputs are well ordered
* Create output markdown file and populate with:
	* Document header (file)
	* Processing metadata (file)
	* Document summary (metadataFile)
* Iterate over the dataframe and add dynamic content to the output markdwon file
	* Overall directory structure
		* Describe folders and the range of suffixes per filetype
	* For each directory in the *processed* folder
		* Summarise the range of suffixes per filetype
		* give a detailed example of a *single* exemplar data file based on filePrefix
			* Create image chips that include for each band
				* Raw image chip
				* Histogram and cumulative histogram
				* Equalized image chip
			* Create True Colour composite for multiband images	
	* For each filePrefix in each of the the *processed* directories
		* Summarise the range of suffixes for that filePrefix
		* give a detailed example of a *single* exemplar data file based on filePrefix
			* Create image chips that include for each band
				* Raw image chip
				* Histogram and cumulative histogram
				* Equalized image chip
			* Create True Colour composite for multiband images			
* Export the final *markdown* file as a pdf using the pandoc library



