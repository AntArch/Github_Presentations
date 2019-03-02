
# Going global: the return of the address wars

##   What characteristics are required for Global Address applications in the 21st century?

Anthony Beck (GeoLytics)

![@address_is_everything_2005](https://farm1.staticflickr.com/24/96618331_2163da240a_z_d.jpg?zz=1)

Unless states otherwise all content is under a CC-BY licence

![](figures/CC_BY.png)

\newpage


```python
## PDF output using pandoc

## For a clean export resetart kernel and clear output

import os


### Export this notebook as markdown
commandLineSyntax = 'ipython nbconvert --to markdown 20190306_Global_Address_Wars_Presentation.ipynb'
print (commandLineSyntax)

os.system(commandLineSyntax)

### Export this notebook and the document header as PDF using Pandoc

commandLineSyntax = 'pandoc  -f markdown -t latex -N -V geometry:margin=1in DocumentHeader.md 20190306_Global_Address_Wars_Presentation.md --filter pandoc-citeproc  --latex-engine=xelatex --toc -o 20190306_Global_Address_Wars_Presentation.pdf '

os.system(commandLineSyntax)


```

    ipython nbconvert --to markdown 20190306_Global_Address_Wars_Presentation.ipynb





    0



To convert and run this as a static presentation run the following command:


```python
# Notes don't show in a python3 environment

!jupyter nbconvert 20190306_Global_Address_Wars_Presentation.ipynb --to slides --post serve
```

To close this instances press *control 'c'* in the *ipython notebook* terminal console

Static presentations allow the presenter to see *speakers notes* (use the 's' key)

If running dynamically run the scripts below


```python
#Future proof python 2
from __future__ import print_function #For python3 print syntax
from __future__ import division

# def
import IPython.core.display

# A function to collect user input - ipynb_input(varname='username', prompt='What is your username')

def ipynb_input(varname, prompt=''):
        """Prompt user for input and assign string val to given variable name."""
        js_code = ("""
            var value = prompt("{prompt}","");
            var py_code = "{varname} = '" + value + "'";
            IPython.notebook.kernel.execute(py_code);
        """).format(prompt=prompt, varname=varname)
        return IPython.core.display.Javascript(js_code)
    
# inline

%pylab inline
```

\newpage

## About me

 

![It's all about me - details about Anthony Beck](figures/Geolytics_ARB_Banner.png)

* Honorary Research Fellow, University of Nottingham: [orcid](http://orcid.org/0000-0002-2991-811X)
* Director, Geolytics Limited - A spatial data analytics consultancy

## About this presentation

* [Available on GitHub](https://github.com/AntArch/Presentations_Github/tree/master/20190306_BCS_Scotland_Presentation) - https://github.com/AntArch/Presentations_Github/
* [Fully referenced PDF](https://github.com/AntArch/Presentations_Github/blob/master/20190306_BCS_Scotland_Presentation/20190306_Global_Address_Wars.pdf)

\newpage

# Addresses

## are part of the fabric of everyday life

![@kaye_map_2012](https://farm9.staticflickr.com/8334/8076658843_bb93c499c9_z_d.jpg)



\newpage

## Have economic and commercial impact

![@flag_of_UPU_2008](https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Flag_of_UPU.svg/640px-Flag_of_UPU.svg.png)



\newpage

## Support governance and democracy

![@appelo_governance_2010](https://farm6.staticflickr.com/5204/5201270923_f02844bb41_z_d.jpg)

* Addresses are a pre-requisite for citizenship in many countries. 
* Without citizenship individuals are excluded from:
	* public services 
	* formal institutions.
* This impacts on democracy. 

\newpage

## Support Legal and Social integration

![@beck_social_integration_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Stufen_Schulischer_Integration_enGB.svg/500px-Stufen_Schulischer_Integration_enGB.svg.png)

* Formal versus Informal
* Barring individuals and businesses from systems:
	* financial
	* legal
	* government
	* ....

\newpage

## Provide spatial structure.

![@walking_1992](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Walking_away_from_the_Third_World.jpg/640px-Walking_away_from_the_Third_World.jpg)

* This helps to identify, locate and access marginalized areas.

\newpage

## Bridge gaps

![](figures/AdressesProvidePeopleWithPlace.png)

provide the link between ***people*** and ***place***

\newpage

# What is an address?

##  Address abstraction

* Address did not spring fully formed into existance. 
* They are used globally
	* but developed nationally
	* and for different reasons

\newpage

## Address abstraction

![@AddressAbstraction_beck_2016](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Postal_Address_Abstraction.svg/1024px-Postal_Address_Abstraction.svg.png)

\newpage

## In the beginning ...... was the ledger, the register, the record

![@ledger_en_beck_2016](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Everton_1933_FA_Cup_team_selection_ledger.JPG/681px-Everton_1933_FA_Cup_team_selection_ledger.JPG)

\newpage

## Then came formalisation

* Local Land and Property Gazetteers and Registers
* Mail
* Address Base
* The World Bank
* Etc.........

Let's look at some

\newpage

###  Korea: The Jibeon system - taxation

* Until recently, the Republic of Korea (Korea) has used land parcel referening (jibeon) 
    * Parcels are assigned chronologically according to date of construction. 
    * **No local predictability**.

![after (@_addressing_2012, p.57)](figures/JibeonAddressingUPU_pg57.png)


* Until recently, the Republic of Korea (Korea) has used land parcel numbers ( jibeon) to identify unique locations. 
    * These parcel numbers were assigned chronologically according to date of construction and without reference to the street where they were located. 
    * This meant that adjacent buildings did not necessarily follow a sequential numbering system.
* This system was initially used to identify land for census purposes and to levy taxes. 
* In addition, until the launch of the new addressing system, the jibeon was also used to identify locations (i.e. a physical address). 

\newpage


### UK Addressing  Geoplace - Formal

![[Geoplace graphic](https://www.geoplace.co.uk/documents/10181/67776/NAG+infographic/835d83a5-e2d8-4a26-bc95-c857b315490a?t=1434370410424)](https://www.geoplace.co.uk/documents/10181/67776/NAG+infographic/835d83a5-e2d8-4a26-bc95-c857b315490a?t=1434370410424)


* GeoPlace is a limited liability partnership owned equally by the [Local Government Association](http://www.local.gov.uk/) and [Ordnance Survey](http://www.ordnancesurvey.co.uk/). 
* It has built a synchronised database containing spatial address data from 
    * 348 local authorities in England and Wales (the *Local Land and Property Gazetteers* (LLPG) which cumulatively create the *National Land and Property Gazetteer* (NLPG)), 
    * Royal Mail, 
    * Valuation Office Agency and 
    * Ordnance Survey datasets. 
* The NAG Hub database is owned by GeoPlace and is the authoritative single source of government-owned national spatial address information, containing over 225 million data records relating to about 34 million address features. GeoPlace is a production organisation with no product sales or supply operations. 
* The NAG is made available to public and private sector customers through Ordnance Survey’s [AddressBase](http://www.ordnancesurvey.co.uk/business-and-government/products/addressbase.html) products.

\newpage

###  The AddressBase Family

![[Ordnance Survey graphic](http://demos.ordnancesurvey.co.uk/public/demos/products/AddressBase/images/database_3_0.jpg)](http://demos.ordnancesurvey.co.uk/public/demos/products/AddressBase/images/database_3_0.jpg)



* The National Address Gazetteer Hub database is owned by GeoPlace and is claimed to be *the authoritative single source of government-owned national spatial address information*, containing over 225 million data records relating to about 34 million address features. 
* Each address has its own *Unique Property Reference Number* (UPRN). The AddressBase suite have been designed to integrate into the [Ordnance Survey MasterMap suite of products](http://www.ordnancesurvey.co.uk/business-and-government/products/mastermap-products.html). 

AddressBase is available at three levels of granularity (lite, plus and premium). 

* AB+ merges two address datasets together (PAF and Local Authority) to provide the best available view of addresses currently defined by Local Authorities, giving many advantages over AddressBase.
* AB+ lets you link additional information to a single address, place it on a map, and carry out spatial analysis that enables improved business practices.
* Geoplace argue that further value comes from additional information in the product which includes:
	* A more detailed classification – allowing a better understanding of the type (e.g. Domestic, Commercial or Mixed) and function of a property (e.g.  Bank or Restaurant)
	* Local Authority addresses not contained within PAF – giving a more complete picture of the current addresses and properties (assuming they are in scope (see below))
	* Cross reference to OS MasterMap TOIDs – allowing simple matching to OS MasterMap Address Layer 2, Integrated Transport Network or Topography Layer
	* Spatial coordinates
	* Unique Property Reference Number (UPRN) – which provides the ability to cross reference data with other organisations, and maintain data integrity.
* Premium includes the address lifecycle


AddressBase supports the UK Location Strategy concept of a 'core reference geography', including the key principles of the European Union INSPIRE directive, that data should only be collected once and kept where it can be maintained most effectively (see [AddressBase products user guide](http://www.ordnancesurvey.co.uk/docs/user-guides/addressbase-products-user-guide.pdf)). *It's probably worthwhile mentioning that this is not an open address layer - however, a [2104 feasibility study sponsored by the department of Business, Innovation and Skills](https://www.gov.uk/government/publications/an-open-national-address-gazetteer) included a recommendation that AddressBase lite is made openly available*.

\newpage

### Royal Mail - Access and Delivery points

![Access Points and Delivery Points](figures/1S_ADP_creating_AP_DP.gif)

\newpage

###  Denmark: An addressing commons

* Geocoded address infrastructure
* Defined the semantics of purpose
	* what is an address
* Open data
	* an address commons with full stakeholder engagement and participation
    * **There is no such thing as an unmatched address**

![after @lind2008addresses](figures/Lind_AddressesAsAnInfrastructureDenmark_After.png)


* Geocoded address infrastructure
* Defined the semantics of purpose
	* what is an address
* Open data
	* an address commons
* The re-use statistics are staggering:
	* 70% of deliveries are to the private sector, 
	* 20% are to central government
	* 10% are to municipalities.
* Benefits:
	* Efficiencies
	* No duplication
	* Improved confidence
	* Known quality
    * **There is no such thing as an unmatched address**

A credible service providing a mutlitude of efficiencies (@_addressing_2012, pp.50 - 54)

\newpage

### The World Bank

![@world_bank_address_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/World_Bank_Recommended_Address_Infrastucture.svg/640px-World_Bank_Recommended_Address_Infrastucture.svg.png)

* Urban bias
* Cost of infrastucture development
* Lack of community involvement

The World Bank has taken a *street addressing* view-point (@_addressing_2012, p.57). This requires up-to-date mapping and bureacracy (to deliver a street gazetteer and to provide the street infrastructure (furniture)). However, (@_addressing_2012, p.44) demonstrates that this is a cumbersome process with a number of issues, not the least:

* Urban bias
* Cost of infrastucture development
* Lack of community involvement

\newpage

# Addressing issues


* Addresses are increasingly over-loaded
	* Assets as addresses
	* Services as addresses
	* People as/at addresses
* Addresses as things

![[Public domain image](https://commons.wikimedia.org/wiki/File:Mono_pensador.jpg)](https://upload.wikimedia.org/wikipedia/commons/0/0d/Mono_pensador.jpg)

\newpage

## Issues: addresses = postal address.

* Is *Postal* a constraining legacy?
* Is *address* a useful term? 

![[Public domain image](https://commons.wikimedia.org/wiki/File:Mono_pensador.jpg)](https://upload.wikimedia.org/wikipedia/commons/0/0d/Mono_pensador.jpg)

\newpage

# Taking stock

##  Addresses are heterogeneous

In terms of:

* What they mean
* What they are used for
* Who uses them
* How they are accessed

![@world_addressing_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Addressing_around_the_world.svg/640px-Addressing_around_the_world.svg.png)



\newpage

##  Assets can have addresses

So - anything can have an address (the *Internet of Things*)

![[Post box](http://joncruddas.org.uk/sites/joncruddas.org.uk/files/styles/large/public/field/image/post-box.jpg?itok=ECnzLyhZ)](http://joncruddas.org.uk/sites/joncruddas.org.uk/files/styles/large/public/field/image/post-box.jpg?itok=ECnzLyhZ)

\newpage

##  National data silos

* They have been created to solve national issues.
    * Applying different paradigms
    * Are *relative referencing system* that do not implicitly provide an accurate spatial location.
* No unifying semantics.

![@IslandsOfData_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Islands_Of_Data.svg/636px-Islands_Of_Data.svg.png)

\newpage

##  Licence silos

![@IncompatibilitiesAndLicenceClauses_en_beck_2016](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Incompatibilities_And_Licence_Clauses.svg/989px-Incompatibilities_And_Licence_Clauses.svg.png)

\newpage

##  Addresses are bureaucratic and costly

![@stamp_schnettelker_2013](https://farm3.staticflickr.com/2819/9786091286_e85fd01bb8_z_d.jpg)

Severely protracted when formal/informal issues are encountered.

\newpage

##  Addresses can be opaque

![@processing_transparency_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Processing_transparency_between_open_and_closed_systems.svg/630px-Processing_transparency_between_open_and_closed_systems.svg.png)

**transparent reproducibility critical for those at the beginning and end of the addressing lifecycle**

\newpage

##  Addresses are of global significance

![@services_products_Gray_2011](https://farm7.staticflickr.com/6213/6296605302_9745b5e72e_z_d.jpg)

\newpage

##  Addresses are ripe for disruption

![@earth_egg_rain_2007](https://farm3.staticflickr.com/2159/2047910540_82620d9481_z_d.jpg?zz=1)

\newpage

# What about the address disenfranchised?


> It is almost impossible for individuals to be part of society without a legal identity. 

> 4 billion people are excluded from the rule of law because they do not have a legal identity, and that **establishing such an identity often depends on having an official address**.

> Addresses appear to be a key element in aiding the delivery of policies at national and international levels ....

@_addressing_2012 p. 6

... particularly with regard to:

* governance
* rule of law
* poverty reduction
* disease prevention
* the provision of basic services such as:
	* electricity
	* sanitation
	* water.

@_addressing_2012 p. 6

> This century is witnessing a fundamental change in our way of life; for the first time in history, half of the world’s population lives in towns and cities. 

> Urban areas are growing faster in developing countries, mostly **through informal settlements.**

> The lack of an address, particularly in informal settlements, can also mean the lack of legal identity, equal opportunities for employment and social integration.

@_addressing_2012 p. 6

Addresses are becoming a ***basic human right***.

\newpage

## The World Bank have a plan

![@world_bank_address_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/World_Bank_Recommended_Address_Infrastucture.svg/640px-World_Bank_Recommended_Address_Infrastucture.svg.png)

\newpage

## But in Africa:

![@stats_africa_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/4/40/UPU_statistics_about_Africa.svg/640px-UPU_statistics_about_Africa.svg.png)

It's difficult to do street based addressing when there are no streets!

The mapping of informal settlements in urban area implies legitamacy - hence it's not done!

And this does exacerbate the urban rural divide.

\newpage

## Legitimacy

![@beck_social_integration_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Stufen_Schulischer_Integration_enGB.svg/500px-Stufen_Schulischer_Integration_enGB.svg.png)

Formal and informal barriers are profound


\newpage

# What are the aspirations for a global addressing framework?

Or an addressing commons?

![@flag_of_UPU_2008](https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Flag_of_UPU.svg/640px-Flag_of_UPU.svg.png)

\newpage

##  It will need to harmonise the formal and informal

![@formalinformal_beck_2016](figures/FormalVersusInformalKnowledgeRepositoriesWithODI.png)

\newpage

## It should meet the needs of the rural and urban communities equally

![@farm_city_Bauschardt_2010](https://farm5.staticflickr.com/4117/4778763329_4ef8706836_b_d.jpg)

\newpage

## It should be lightweight and cheap to implement

![@stamp_schnettelker_2013](https://farm3.staticflickr.com/2819/9786091286_e85fd01bb8_z_d.jpg)


\newpage

## It should be transparent, reproducible and predictable

![@processing_transparency_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Processing_transparency_between_open_and_closed_systems.svg/630px-Processing_transparency_between_open_and_closed_systems.svg.png)

\newpage

## It should be born spatial and global

An address system should not require specific geocoding services to make it spatial.

Streets are so last century.....

![@world_bank_address_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/World_Bank_Recommended_Address_Infrastucture.svg/640px-World_Bank_Recommended_Address_Infrastucture.svg.png)

* Ubiquitous GPS/GNSS
* Structured crowdsourced geo-enabled content (wikipedia, OSM)


\newpage

## It should be an openly licenced Core Reference data set

The situation is best summarised by the open access Danish addressing commons [@_addressing_2012 p. 54]:

![after @lind2008addresses](figures/Lind_AddressesAsAnInfrastructureDenmark_After.png)

The re-use statistics are staggering:
* 70% of deliveries are to the private sector, 
* 20% are to central government
* 10% are to municipalities.

**There is no such thing as an unmatched address**.

\newpage

## It should be accessible (on and off-line)

![Plugged in](figures/Plug_interoperability.svg.png)

\newpage

## It should support and enhance business services

![@services_products_Gray_2011](https://farm7.staticflickr.com/6213/6296605302_9745b5e72e_z_d.jpg)

\newpage

## It should support many ways of engagement

![Public domain image from [The Love Talk Project](https://commons.wikimedia.org/wiki/File:Love_talk_-_The_Noun_Project.svg)](https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/Love_talk_-_The_Noun_Project.svg/480px-Love_talk_-_The_Noun_Project.svg.png)

[What3Words completely get this!](https://player.fm/series/local-to-global-with-nick-hewer/reinventing-the-postcode-with-what3words)

\newpage

# A new global address paradigm?  

* [Amazon drone delivery in the UK requires](https://www.theguardian.com/technology/2016/jul/25/amazon-to-test-drone-delivery-uk-government)
	* A new view over addressing complements streets and buildings but is geo-coded at source
	* and supports accurate delivery throughout the delivery chain using a global referencing system.

Is there a universal approach which allows all avenues to be satisfied?

![[Amazon drone delivery in the UK requires](https://www.theguardian.com/technology/2016/jul/25/amazon-to-test-drone-delivery-uk-government)](figures/Guardian_Amazon_drone.png)


\newpage

#  How might this look? CORE

.
.

**MUST HAVE** Core requirements for a Global Address Framework

.
.

\newpage

##  WGS84 algorithmic address minting

* **Born spatial**
* **Accessible**
* **Lightweight and cheap to implement**
* **Transparent, reproduceable and predicatable**

![Addressing minting: @minting_addresses_2009](https://farm3.staticflickr.com/2432/3832442378_bf76a81b5d_d.jpg)





\newpage

##  Small footprint

* **Accessible**
* **Lightweight and cheap to implement**

![Small footprints: @small_footprints_terwolbeck_2012](https://farm8.staticflickr.com/7185/6988489897_282270cfd5_z_d.jpg)



\newpage

##  Short/memorable

**Support and enhance business services**

![@mnemonics_munroe_nd](http://imgs.xkcd.com/comics/mnemonics.png)

\newpage

##  Self checking 

* **Support and enhance business services**

![@parity_levine_2014](https://farm6.staticflickr.com/5576/14117894364_a3715fdfce_z_d.jpg)



\newpage

## Unlimited spatial recording

* **Support and enhance business services**
* **Formal and informal, Rural and Urban**
    * What are the spatial requirements for the range of addressing options?
        * [Manila has a population density of 42,857 people per square km](http://en.wikipedia.org/wiki/List_of_cities_proper_by_population_density). 
        * [Map Kibera](http://mapkibera.org/) and OSM has revolutionised service delivery in Kibera (Kenya). 
            * Address Kibera could do the same thing for citizenship.

![@geodesic_grid_petersen_2007](http://upload.wikimedia.org/wikipedia/en/thumb/f/fd/Geodesic_Grid_%28ISEA3H%29_illustrated.png/640px-Geodesic_Grid_%28ISEA3H%29_illustrated.png)



\newpage

## Open and interoperable

* **Transparent, reproduceable and predicatable**
* **Openly Licensed**

![](figures/PromotingInteroperability.png)



\newpage

> the lack of a consistent and transparent legal and policy framework for sharing spatial data continues to be an additional roadblock.

@pomfret_spatial_2010

\newpage

#  How might this look? Nice to haves

.
.

**Would be nice to have** extended requirements for a Global Address Framework

.
.

\newpage

##  Indoor use and 3D

* **Support and enhance business services**
* Incorporating wifi-triangulation - *individual room* addressing and navigation.
* Seamless integration with BIM and CityGML.
* *Addressing isn't only about buildings and 2D - think 3D and the Internet of Things*

![@bim_arup_2013](https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Outsourcing-bim-integration-construction.jpg/640px-Outsourcing-bim-integration-construction.jpg)



\newpage

##  Inherent geo-statistical aggregation (spatially scalable)

* **Support and enhance business services**
* GIS free multi-scale analysis and reporting during disaster scenarios.

![How spatial resolution impacts on feature detection @spatial_resolution_2012](https://upload.wikimedia.org/wikipedia/commons/thumb/6/63/Spatial_resolution_comparison_for_archaeological_features.svg/1024px-Spatial_resolution_comparison_for_archaeological_features.svg.png)



\newpage

## Area representation based on a regular tessellation

* **Support and enhance business services**
    * It is still useable within traditional GIS.

![[Public domain image](https://commons.wikimedia.org/wiki/File:Tesselation_pipeline.svg)](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Tesselation_pipeline.svg/800px-Tesselation_pipeline.svg.png)




\newpage

## Spatial adjacency relations within the encoding

* **Support and enhance business services**
    * Understanding localised connectivity relations.

![@rcc8_beck_2013](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/Region_Connection_Calculus_8_Relations_and_Open_Geospatial_Consortium_relations.svg/640px-Region_Connection_Calculus_8_Relations_and_Open_Geospatial_Consortium_relations.svg.png)




\newpage

# What do you want your technology candidates to do?

BCS examples (in alphabetical order):

* [GeoHash](http://en.wikipedia.org/wiki/Geohash)
	* [gcpvj1r2vnbp](http://geohash.org/gcvwr2mkkhe1)
* [Maidenhead Locator System](http://en.wikipedia.org/wiki/Maidenhead_Locator_System)
	* IO85jw (it has a very large footprint)
* [MapCode](http://www.mapcode.com/)
	* GBR 8PJ.TJ	
* [Natural Area Code](http://nactag.info/map.asp)
	* GQ0X1 S9PNR
* [What3Words](http://what3words.com/)
	* [assume.calms.union](https://map.what3words.com/assume.calms.union)



\newpage

## Combining frameworks

* One size doesn't have to fit all.
* Build bridges between Global and National frameworks
* Understand fitness for purpose for each application

![A [public domain image](https://commons.wikimedia.org/wiki/File:Duimstok_50cm.jpg)](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Duimstok_50cm.jpg/640px-Duimstok_50cm.jpg)



\newpage

![Righs reserved](figures/Addressing_Concept_RosettaStone.png)



\newpage

## Q. How do we encourage such infrastructure development?

![@services_products_Gray_2011](https://farm7.staticflickr.com/6213/6296605302_9745b5e72e_z_d.jpg)



\newpage

## A. Support [core reference geographies](http://www.slideshare.net/geocommunitylive/bob-barr-what-are-core-reference-geographies)

Bob Barr has described [core reference geographies](http://www.slideshare.net/geocommunitylive/bob-barr-what-are-core-reference-geographies) as geographic data which:

* Are definitive
* Should be collected and maintained once and used many times
* Are Natural monopolies (which addresses are)
* Have variable value in different applications
* Have highly elastic demand

**Global addresses are a core reference geography.**



\newpage

## Wrap up.... A GeoCommons core supporting formal and informal services

What if global addressing, as a core reference geography, was an inclusive loosely coupled GeoCommons......... 

![after @lind2008addresses](figures/GeoCommons_RosettaStone.svg.png)



\newpage

## Questions

 

![It's all about me - details about Anthony Beck](figures/Geolytics_ARB_Banner.png)


```python

```
