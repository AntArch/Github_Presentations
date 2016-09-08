![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/Interoperability
SemanticsAndOpenData.png)


Go down for licence and other metadata about this presentation

\newpage

# Preamble

## Licence

Unless stated otherwise all content is released under a [CC0]+BY licence. I'd
appreciate it if you reference this but it is not necessary.

![](https://dl.dropboxusercontent.com/u/393477/SharedPresentations/Shared_HTML5/
Images/CC_BY.png)

\newpage

## Using Ipython for presentations

A short video showing how to use Ipython for presentations

```python
from IPython.display import YouTubeVideo
YouTubeVideo('F4rFuIb1Ie4')
```

```python
## PDF output using pandoc

import os


### Export this notebook as markdown
commandLineSyntax = 'ipython nbconvert --to markdown 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb'
print (commandLineSyntax)

os.system(commandLineSyntax)

### Export this notebook and the document header as PDF using Pandoc

commandLineSyntax = 'pandoc  -f markdown -t latex -N -V geometry:margin=1in DocumentHeader.md 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.md --filter pandoc-citeproc  --latex-engine=xelatex --toc -o interim.pdf '

os.system(commandLineSyntax)

### Remove cruft from the pdf

commandLineSyntax = 'pdftk interim.pdf cat 1-5 18-end output 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.pdf'

os.system(commandLineSyntax)

### Remove the interim pdf

commandLineSyntax = 'rm interim.pdf'

os.system(commandLineSyntax)
```

## The environment

In order to replicate my environment you need to know what I have installed!

### Set up watermark

This describes the versions of software used during the creation.

Please note that critical libraries can also be watermarked as follows:

```python
%watermark -v -m -p numpy,scipy
```

```python
%install_ext https://raw.githubusercontent.com/rasbt/python_reference/master/ipython_magic/watermark.py
%load_ext watermark

```

```python
%watermark -a "Anthony Beck"  -d -v -m -g
```

```python
#List of installed conda packages
!conda list
```

```python
#List of installed pip packages
!pip list
```

## Running dynamic presentations

You need to install the [RISE Ipython
Library](https://github.com/damianavila/RISE) from [Damián
Avila](https://github.com/damianavila) for dynamic presentations

To convert and run this as a static presentation run the following command:

```python
# Notes don't show in a python3 environment

!ipython nbconvert 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb --to slides --post serve


```

To close this instances press *control 'c'* in the *ipython notebook* terminal
console

Static presentations allow the presenter to see *speakers notes* (use the 's'
key)

If running dynamically run the scripts below

## Pre load some useful libraries

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



![It's all about me - details about Anthony Beck](https://dl.dropboxusercontent.
com/u/393477/ImageBank/Geolytics_ARB_Banner.png)

* Honorary Research Fellow, University of Nottingham:
[orcid](http://orcid.org/0000-0002-2991-811X)
* Director, Geolytics Limited - A spatial data analytics consultancy

## About this presentation

* [Available on GitHub](https://github.com/AntArch/Presentations_Github/tree/mas
ter/20151008_OpenGeo_Reuse_under_licence) -
https://github.com/AntArch/Presentations_Github/
* [Fully referenced PDF](https://github.com/AntArch/Presentations_Github/blob/ma
ster/20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOp
enData/20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAnd
OpenData.pdf)


\newpage

# Contribution to GIScience learning outcomes

This presentation contributes to the following learning outcomes for this
course.

1. Knowledge and Understanding:
        * Appreciate the importance of standards for Geographic Information and
the role of the Open Geospatial Consortium.
        * Understand the term 'interoperability'.
        * Appreciate the different models for database design.
        * Understand the basis of Linked Data.
        * Find UK government open data and understand some of the complexities
in the use of this data.
        * Appreciate the data issues involved in managing large distributed
databases, Location-Based Services and the emergence of real-time data gathering
through the 'Sensor-Web'.
        * Understand the different models for creating international Spatial
Data Infrastructures.
1. Intellectual Skills:
        * Evaluate the role of standards and professional bodies in GIS.
        * Articulate the meaning and importance of interoperability, semantics
and ontologies.
        * Assess the technical and organisational issues which come into play
when attempting to design large distributed geographic databases aimed at
supporting 'real-world' problems.



# A potted history of mapping

## In the beginning was the geoword


and the word was ***cartography***


![The lens of cartography @TheLensOfCartography_beck_2015](https://upload.wikime
dia.org/wikipedia/commons/thumb/8/85/TheLensOfCartography.svg/1024px-
TheLensOfCartography.svg.png)


\newpage

![A static map (public domain) encapsulating spatial knowledge in a portable
manner](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0
/Claudius_Ptolemy-_The_World.jpg/1024px-Claudius_Ptolemy-_The_World.jpg)

* Cartography was king.
* Static representations of spatial knowledge with the cartographer deciding
what to represent.
    * Hence, maps are domain specific knowledge repositories for spatial data

\newpage

# And then there was data .........




![Data @Data_types_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/
thumb/6/6d/Data_types_-_en.svg/576px-Data_types_-_en.svg.png)

\newpage

![But the data was siloed (restricted use)](https://dl.dropboxusercontent.com/u/
393477/ImageBank/ForOGC/TheEndOfThe20thCentury.png)

Restrictive data

\newpage

![The implications of a landscape of silo-ed data @IslandsOfData_en_beck_2015](h
ttps://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Islands_Of_Data.svg
/1017px-Islands_Of_Data.svg.png)

Disconnected data with different:

* Standards
* Quality
* Databases
* Semantics

\newpage

# Why is this an issue?

Over to you......





* Decision Making
    * certainty
    * uncertainty
* Co-ordination
* Policy formation
* Efficiencies
* Best Practice


\newpage

# [INSPIRE](http://inspire.ec.europa.eu/)



```python
from IPython.display import YouTubeVideo
YouTubeVideo('xew6qI-6wNk')

```

\newpage

# INSPIRE principles

* Data should be collected only once and kept where it can be maintained most
effectively
* It should be possible to combine seamless spatial information from different
sources across Europe and share it with many users and applications
* It should be possible for information collected at one level/scale to be
shared with all levels/scales; detailed for thorough investigations, general for
strategic purposes
* Geoinformation needed for good governance at all levels should be readily and
transparently available
* Easy to find what geoinformation is available, how it can be used to meet a
particular need, and under which conditions it can be acquired and used

\newpage

![Concerted efforts to de-silo data and make data interoperable (restricted use)
](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/TheCatalyst.png)

Making data interoperable and open

\newpage

# Interoperability

> is a property of a product or system, whose interfaces are completely
understood, to work with other products or systems, present or future, without
any restricted access or implementation.

@wikipedia_interoperability_2016




\newpage

# Technical interoperability - levelling the field

![Interoperable integration of spatial data - the technological issues @Technica
lInteroperableIntegrationOfSpatialData_beck_2015](https://upload.wikimedia.org/w
ikipedia/commons/thumb/5/53/TechnicalInteroperableIntegrationOfSpatialData.svg
/1024px-TechnicalInteroperableIntegrationOfSpatialData.svg.png)

\newpage

# Syntactic Heterogeneity

> the difference in data format. The same **logical model** can be represented
in a range of different **physical models** (for example ESRI shape file or
Geography Mark-up Language (GML)).

This mismatch between underlying data models implies that the same information
could be represented differently in different organisations.

The most profound difference is in the storage paradigm:

* relational,
* object orientated or
* hybrids.

@beck_uk_2008, @bishr_overcoming_1998


\newpage

# Semantic Heterogeneity

> Semantic heterogeneity refers to differences in naming conventions and
conceptual groupings.

This can be subdivided into **naming** and **cognitive** heterogeneities.

* Naming (synonym) mismatch arises when semantically identical data items are
named differently.
* Cognitive (homonym) mismatch arises when semantically different data items are
named identically.
    * Cognitive semantics can be subtle, reflecting the domain of discourse.

@beck_uk_2008, @bishr_overcoming_1998


\newpage

# Schematic Heterogeneity

> refers to the differences in data model between organisations modelling the
same concepts.

This reflects each organisation’s abstracted view of their business and physical
assets. Hence, different hierarchical and classification concepts are adopted by
each organisation to refer to identical or similar real world objects.

@beck_uk_2008, @bishr_overcoming_1998


\newpage

# The role of the OGC (a geospatial standards body)


* To serve as a global forum for the development, promotion and harmonization of
*open and freely available* **geospatial standards**
* To achieve the full societal, economic and scientific benefits of integrating
electronic location resources into commercial and institutional processes
worldwide.

![The OGC Logo](http://www2.isprs.org/tl_files/isprs/comm2/symposium/Documents/O
GC_logo.png)



\newpage

# The role of the OGC (a geospatial standards body)

OGC’s Open Standards are:

* Freely and publicly available
* Non discriminatory
* No license fees
* Vendor neutral
* Data neutral
* Adopted in a formal, member based consensus process

OGC’s Open Standards are submitted to other industry and National Standards
Development Organisations in the vertical area and to global organisations like
ISO for standard branding.

\newpage

# OGC Technologies

* The OGC publish standards that have been agreed by OGC members
* Current standards can be found at: [http://www.opengeospatial.org/standards](h
ttp://www.opengeospatial.org/standards)
* These are implementation standards
        * written for a more technical audience and detail the interface
structure between software components
* Predicated on abstract specifications
        * the conceptual foundation for most OGC standards development
activities
        * [http://www.opengeospatial.org/specs/?page=abstract](http://www.openge
ospatial.org/specs/?page=abstract)


\newpage

# The main OGC standards

* [WMS – Web Map Service](http://www.opengeospatial.org/standards/wms)
        * Provides rendered images of maps
        * Current version: 1.3
* [WFS – Web Feature Service](http://www.opengeospatial.org/standards/wfs)
        * Provides vector data on demand
        * Current version: 2.0
* [WCS – Web Coverage Service](http://www.opengeospatial.org/standards/wcs)
        * Provides raster data (e.g. satellite data) on demand
        * Current version: 2.0
* [GML – The Geography Markup
Language](http://www.opengeospatial.org/standards/gml)
        * Used as an interoperable standard for transmitting geographic data
(2D, 3D, topology, etc.)
        * Versions 2.1.x and 3.2.1 are most relevant

\newpage

# Other OGC standards

```python
from IPython.display import IFrame
IFrame('http://www.opengeospatial.org/standards', width=1000, height=700)
```

\newpage

# Interoperability in action

![The use of OGC standards in an interoperable multi-data delivery environment @
GeoServerGeoNetworkWithWebApp2013](https://upload.wikimedia.org/wikipedia/common
s/thumb/0/09/GeoServer_GeoNetwork_with_web_app.svg/877px-
GeoServer_GeoNetwork_with_web_app.svg.png)

\newpage

# What did technical interoperability facilitate

![From Map to Model The changing paradigm of map creation from cartography to
data driven visualization @FromMapToModel_beck_2015](https://upload.wikimedia.or
g/wikipedia/commons/thumb/a/a0/FromMapToModel.svg/1024px-FromMapToModel.svg.png)

From Map to Model The changing paradigm of map creation from cartography to data
driven visualization

\newpage

![A new working paradigm (public domain)](https://dl.dropboxusercontent.com/u/39
3477/ImageBank/ForOGC/ANewWorkingParadigm.png)

\newpage

# The world was a happy place.......

Our data was interoperable!

![But time moved on @NonsymmetricVelocity_en_cleonis_2006](https://upload.wikime
dia.org/wikipedia/commons/7/72/Nonsymmetric_velocity_time_dilation.gif)


\newpage

# Then ....... along came **open data**

![open data word cloud of Anthony Beck](https://dl.dropboxusercontent.com/u/3934
77/SharedPresentations/Shared_HTML5/Images/ARB_WordleCloud.png)

\newpage

# The Open landscape integrates **formal** and **informal** data

![Local To Global integration of data to create multiple generic products @Local
_To_Global_integration_of_data_to_create_multiple_generic_products_beck_2015](ht
tps://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Local_To_Global_integrat
ion_of_data_to_create_multiple_generic_products.svg/1024px-
Local_To_Global_integration_of_data_to_create_multiple_generic_products.svg.png)

\newpage

![Cartography is no longer key. Spatial mapping is now about the the formal and
informal data stack. Elements such as provenance, credibility are much more
important for use and re-use of this data. @CartographyNoLongerKing_beck_2015](h
ttps://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/CartographyNoLongerKing
.svg/1024px-CartographyNoLongerKing.svg.png)

\newpage

# Background  - originally a grass roots (community) movement..

![The Open Knowledge Foundation (@Open_Knowledge_logo), Open Street Map
(@Openstreetmap_logo), Wikipedia (@Wikipedia-logo-v2-en) and
OSGeo](https://dl.dropboxusercontent.com/u/393477/ImageBank/Open_logos.png)


Open access to knowledge gained significant momementum with the increased uptake
of the World Wide Web. This is particularly seen in initiatives like
[Wikipedia](https://en.wikipedia.org) (established in 2001) and [Open
Knowledge](https://en.wikipedia.org/wiki/Open_Knowledge) (was the Open Knowledge
Foundation: established in 2004). Within the Geo community [Open Street Map
](https://en.wikipedia.org/wiki/OpenStreetMap) (also established in 2004) and
the [Open Source Geospatial
Foundation](https://en.wikipedia.org/wiki/Open_Source_Geospatial_Foundation)
(OSGeo - established in 2006) are key initiatives that promote accessible data
and software resources respectively.

Critical to this is that these were **grass roots** (community) movements that
have proven to be highly disruptive to incumbent data providers, practices and
policies.

\newpage

# Open in government

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/Interoperability
SemanticsAndOpenData.png)

The impact of these grass roots movements is seen in Open Data (dot) gov.
Pioneered by leaders such as Tim Berners Lee and Nigel Shadbolt

The Shakespeare review [-@shakespeare_shakespeare_2013] indicate that the amount
of government Open Data, at least in the UK, is only going to grow.
Open data has the potential to trigger a revolution in how governments think
about providing services to citizens and how they measure their success: this
produces societal impact.
This will require an understanding of citizen needs, behaviours, and mental
models, and how to use data to improve services.

\newpage

## Valuing Open Data

![McKinsey report valuing *open data* [@mckinsey_open_2013]](https://dl.dropboxu
sercontent.com/u/393477/ImageBank/Mckinsey_Value_of_OpenData.png)

A [McKinsey Global Institute report examines the economic impact of Open Data](h
ttp://www.mckinsey.com/insights/business_technology/open_data_unlocking_innovati
on_and_performance_with_liquid_information) [@mckinsey_open_2013] and estimates
that globally open data could be worth a minimum of $3 trillion annually.

\newpage

# Open in academia

> Open inquiry is at the heart of the scientific enterprise..... Science’s
powerful capacity for self-correction comes from this openness to scrutiny and
challenge.

*Science as an open enterprise* [@royal_society_science_2012 p. 7].

>Science is based on building on, reusing and openly criticising the published
body of scientific knowledge.

>For science to effectively function, and for society to reap the full benefits
from scientific endeavours, it is crucial that science data be made open.

The Panton Principles (@murray-rust_panton_2010) which underpin **Open
Science**.


The Royal Society’s report Science as an open enterprise
[-@royal_society_science_2012] identifies how 21^st^ century communication
technologies are changing the ways in which scientists conduct, and society
engages with, science. The report recognises that ‘open’ enquiry is pivotal for
the success of science, both in research and in society.

The Panton Principles pre-cursed this call with a clarion call to the academic
community to open their data and start to conduct **open science**.

![@open_science_does_not_equal_open_access_2013](https://upload.wikimedia.org/wi
kipedia/commons/thumb/7/7c/Open_Science_Does_Not_Equal_Open_Access.svg/1024px-
Open_Science_Does_Not_Equal_Open_Access.svg.png)

This goes beyond open access to publications (Open Access), to include access to
data and other research outputs (Open Data), and the process by which data is
turned into knowledge (Open Science).

## The next generation open data in academia

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/zenodo.png)

Zenodo is a **DATA REPOSITORY** which offers:

* accreditation
* different licences
* different exposure (private (closed), public (open) and embargoed
(timestamped))
* DOIs
* is free at the point of use
* is likely to be around for a long time
    * supported by Horizon 2020 and delivered by CERN



\newpage

# The underlying rationale of Open Data is:

* unfettered access to large amounts of ‘raw’ data
    * enables patterns of re-use and knowledge creation that were previously
impossible.
    * improves transparency and efficiency
    * encourages innovative service delivery
* introduces a range of data-mining and visualisation challenges,
    * which require multi-disciplinary collaboration across domains
    * catalyst to research and industry
* supports the generation of new products, services and markets
* the prize for succeeding is improved knowledge-led policy and practice that
transforms
    * communities,
    * practitioners,
    * science and
    * society


\newpage

# Free and Open Source Software in in Geo

```python
from IPython.display import IFrame
IFrame('http://www.osgeo.org/', width=1200, height=700)
```

\newpage

# So...... we have access to lots of data and software

* Formal and Informal
* Open and Proprietary




# Where are these new data products?

Data, data everywhere - but where are the new derivatives and services?


\newpage

# Interoperability

[The Defense domain are a bit more
explicit......](http://www.dau.mil/pubscats/atl%20docs/jan-feb/watson_jan-
feb10.pdf)

> As defined by DoD policy, interoperability is the ability of systems, units,
or forces to provide data, information, material, and services to, and accept
the same from, other systems, units, or forces; and to use the data,
information, material, and services so exchanged to enable them to operate
effectively together. IT and NSS interoperability includes both the technical
exchange of information and the end-to-end operational effectiveness of that
exchanged information as required for mission accomplishment. Interoperability
is more than just information exchange; it includes systems, processes,
procedures, organizations, and missions over the life cycle and must be balanced
with information assurance.

@watson_joint_2010

\newpage

# Non-technical interoperability issues?



![Islands of incompatibility [@IncompatibilitiesAndLicenceClauses_en_beck_2016]]
(https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Incompatibilities_And
_Licence_Clauses.svg/989px-Incompatibilities_And_Licence_Clauses.svg.png)

\newpage

\newpage

![The full stack that enables interoperable integration of spatial data @Interop
erableIntegrationOfSpatialData_beck_2015](https://upload.wikimedia.org/wikipedia
/commons/thumb/5/5d/InteroperableIntegrationOfSpatialData.svg/500px-
InteroperableIntegrationOfSpatialData.svg.png)

\newpage

# Non-technical interoperability

Issues surrounding non-technical interoperability include:

* Policy interoperabilty
* Licence interoperability
* Legal interoperability
* Social interoperability

We will focus on licence interoperability


\newpage

## Policy Interoperability

The relationship between:

* Individuals
* Organisations
* Countries

Policy determines what, who and how different content can be accessed.

In addition to other elements the policy statements determine:

* Authentication
* Authorization
* Audit



See @innocenti_towards_2011 for more details

\newpage

## Social (or human) Interoperability

Social interoperability is concerned about the environment and business and
human processes.

* Tools are used by people
* The social dimension of operational use is underestimated (it's difficult)
* People form complex inclusive and exclusive networks
    * These operate at many scales

[US Department of Defence researchers have
advocated](http://www.dtic.mil/ndia/2009systemengr/8854WednesdayTrack8Zavin.pdf)
the development of Policy, Standards, and Operational Procedures for:

* forming human networks
* human to human communications
* organization to organization communications
* human system integration
* information sharing across disparate domains:
     * DoD-Coalition-Interagency-intercommunity


\newpage

## Legal Interoperability

> Legal interoperability addresses the process of making legal rules cooperate
across jurisdictions, on different subsidiary levels within a single state or
between two or more states.

(@weber_legal_2014, p. 6)

The [Research Data Alliance](https://rd-alliance.org/) state that [legal
interoperability occurs among multiple datasets when](https://rd-
alliance.org/group/rdacodata-legal-interoperability-ig/wiki/legal-principles-
data.html):

* use conditions are clearly and readily determinable for each of the datasets,
* the legal use conditions imposed on each dataset allow creation and use of
combined or derivative products, and
* users may legally access and use each dataset without seeking authorization
from data rights holders on a case-by-case basis, assuming that the accumulated
conditions of use for each and all of the datasets are met.

Legal interoperability also implies that the search for or tracking of licenses
or other legal instruments and their compatibility with other legal conditions
will occur in online environments.

\newpage

### Licence Interoperability

A specific form of legal interoperability

\newpage

# Example of applying the semantic web to licence interoperability

![The modern data landscape
(restricted)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC
/20151008_Re-UseUnderLicence.png)

There is a multitude of formal and informal data.

\newpage

## What is a licence?

[Wikipedia state:](https://en.wikipedia.org/wiki/License)

> A license may be granted by a party ("licensor") to another party ("licensee")
as an element of an agreement between those parties.

> A shorthand definition of a license is "an authorization (by the licensor) to
use the licensed material (by the licensee)."



![Some licences @rdflicense_2015](https://dl.dropboxusercontent.com/u/393477/Ima
geBank/ForOGC/SomeLicences_FromRDFLicences.png)

Each of these data objects can be licenced in a different way. This shows some
of the licences described by the RDFLicence ontology

\newpage

```python
### Export this notebook as markdown
commandLineSyntax = 'dot -Tpng FCA_ConceptAnalysis.dot > FCA_ConceptAnalysis.png'
commandLineSyntax = 'dot -Tsvg FCA_ConceptAnalysis.dot > FCA_ConceptAnalysis.svg'
print (commandLineSyntax)

os.system(commandLineSyntax)

```

![Concepts surrounding licences (derived from Formal Concept
Analysis)](http://g.gravizo.com/g?
 digraph graphname {
     a [label="No derivation"];
     b [label="No Distribution and modification"];
     c [label="Any"];
     d [label="Read"];
     e [label="Distribution"];
     f [label="Modification"];
     g [label="Reproduction"];
     h [label="Present"];
     i [label="Sell"];
     j [label="Grant Use"];
     k [label="Include attribution"];
     l [label="Commercial use"];
     m [label="Public"];
     n [label="Share alike"];
     o [label="None"];
     p [label="No commercial use"];
     q [label="Derivation"];
     r [label="Include source"];
     s [label="Copyleft"];
     t [label="Include licence"];
     u [label="All reserved"];
     a -> c -> d -> j -> m -> o -> u -> a;
     u -> b -> c;
     c -> t -> s -> o -> p -> q -> l -> o;
     o -> n -> q -> j -> i -> g -> k -> l -> e -> c -> g -> h -> j -> f -> e ->
r -> g;
     r -> s;
 }
)

![Concepts surrounding licences (derived from Formal Concept Analysis)](https://
dl.dropboxusercontent.com/u/393477/ImageBank/FCA_ConceptAnalysis.png)

Concepts (derived from Formal Concept Analysis) surrounding licences

\newpage

Two lead organisations have developed legal frameworks for content licensing:

* [Creative Commons (CC)](https://creativecommons.org/) and
* [Open Data Commons (ODC)](http://opendatacommons.org/).

Until the release of [CC version 4](https://wiki.creativecommons.org/4.0),
published in November 2013, the CC licence did not cover data. Between them, CC
and ODC licences can cover all forms of digital work.

* **There are many other licence types**
* Many are bespoke
    * Bespoke licences are difficult to manage
    * Many legacy datasets have bespoke licences

![Creative Commons @love_CC_2008](https://farm4.staticflickr.com/3148/2732488224
_aedf36e837_b_d.jpg)

I'll describe CC in more detail

\newpage

## Creative Commons Zero

Creative Commons Zero (CC0) is essentially public domain which allows:

* Reproduction
* Distribution
* Derivations




\newpage

### Constraints on CC0

The following clauses constrain CC0:

* Permissions
    * ND – No derivatives: the licensee can not derive new content from the
resource.
* Requirements
    * BY – By attribution: the licensee must attribute the source.
    * SA – Share-alike: if the licensee adapts the resource, it must be released
under the same licence.
* Prohibitions
    * NC – Non commercial: the licensee must not use the work commercially
without prior approval.




### CC license combinations

License|Reproduction|Distribution|Derivation|BY|SA|NC
----|----|----|----|----|----|----
CC0|X|X|X|||
CC-BY-ND|X|X||X||
CC-BY-NC-ND|X|X||X||X
CC-BY|X|X|X|X||
CC-BY-SA|X|X|X|X|X|
CC-BY-NC|X|X|X|X||X
CC-BY-NC-SA|X|X|X|X|X|X


Table: [Creative Commons license combinations](https://docs.google.com/spreadshe
ets/d/17aT7Dj6QtE88XPS44oPQ7mVeSdY1YnZ1rlpjPvXNz0E/pub?single=true&gid=0&output=
html)

\newpage

# Why are licenses important?

* They tell you what you can and can't do with 'stuff'
* Very significant when multiple datasets are combined
    * It then becomes an issue of license compatibility


![Compatibility of common open-source software licenses @Floss-license-slide-
image_Wheeler_2007](https://upload.wikimedia.org/wikipedia/commons/1/1d/Floss-
license-slide-image.png)

\newpage

## Which is important when we mash up data

Certain licences when combined:

* Are incompatible
    * Creating data islands
* Inhibit commercial exploitation (NC)
* Force the adoption of certain licences
    * If you want people to commercially exploit your stuff don't incorporate
CC-BY-NC-SA data!
* Stops the derivation of *new works*



\newpage

![Islands of incompatibility [@IncompatibilitiesAndLicenceClauses_en_beck_2016]]
(https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Incompatibilities_And
_Licence_Clauses.svg/989px-Incompatibilities_And_Licence_Clauses.svg.png)

\newpage

![A conceptual licence processing workflow @ConceptualLicenceProcessingWorkflow_
beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/ConceptualL
icenceProcessingWorkflow.svg/1024px-ConceptualLicenceProcessingWorkflow.svg.png)


A conceptual licence processing workflow. The licence processing service
analyses the incoming licence metadata and determines if the data can be legally
integrated and any resulting licence implications for the derived product.

\newpage

# A rudimentry logic example

```
Data1 hasDerivedContentIn NewThing.

Data1 hasLicence a cc-by-sa.

What hasLicence a cc-by-sa? #reason here

If X hasDerivedContentIn Y and hasLicence Z then Y hasLicence Z. #reason here

Data2 hasDerivedContentIn NewThing.

Data2 hasLicence a cc-by-nc-sa.

What hasLicence a cc-by-nc-sa? #reason here

Nothing hasLicence a cc-by-nc-sa and hasLicence a cc-by-sa. #reason here
```


And processing this within the Protege reasoning environment

```python
from IPython.display import YouTubeVideo
YouTubeVideo('jUzGF401vLc')
```

\newpage

## Here's something I prepared earlier

A live presentation (for those who weren't at the event).....

```python
from IPython.display import YouTubeVideo
YouTubeVideo('tkRB5Rp1_W4')

```

\newpage

# A more robust logic

* Would need to decouple licence incompatibility from licence name into licence
clause (see table below)
* Deal with all licence type
* Provide recommendations based on desired derivative licence type
* Link this through to the type of process in a workflow:
    * data derivation is, from a licence position, very different to contextual
display

License|Reproduction|Distribution|Derivation|BY|SA|NC
----|----|----|----|----|----|----
CC0|X|X|X|||
CC-BY-ND|X|X||X||
CC-BY-NC-ND|X|X||X||X
CC-BY|X|X|X|X||
CC-BY-SA|X|X|X|X|X|
CC-BY-NC|X|X|X|X||X
CC-BY-NC-SA|X|X|X|X|X|X
ODC-PDDL|X|X|X|||
ODC-BY|X|X|X|X||
ODC-ODbL|X|X|X|X|X|
OGL 2.0|X|X|X|X||
OS OpenData|X|X|X|X|?|

Table: [Creative Commons license combinations](https://docs.google.com/spreadshe
ets/d/17aT7Dj6QtE88XPS44oPQ7mVeSdY1YnZ1rlpjPvXNz0E/pub?single=true&gid=0&output=
html)


\newpage

# OGC and Licence interoperability

* The geo business landscape is increasingly based on integrating heterogeneous
data to develop new products
* Licence heterogeneity is a barrier to data integration and interoperability
* A licence calculus can help resolve and identify heterogenties leading to
    * legal compliance
    * confidence
* Use of standards and collaboration with organisations is crucial
    * [Open Data Licensing ontology](https://github.com/theodi/open-data-
licensing)
    * [The Open Data Institute](http://theodi.org/)
* Failure to do this could lead to breaches in data licenses
    * and we all know where that puts us........



![Breaching a data license can be serious (restricted = randomly!)](https://dl.d
ropboxusercontent.com/u/393477/ImageBank/Jail_Bars_Icon.png)

\newpage

# Linked data and the Semantic Web

## The web of Documents

* a global filesystem
* Designed for human consumption
* Primary objects are documents
* Expresses links between documents (or sub-parts of)
* Degree of structure in objects is fairly low
* Semantics of content and links is implicit



## The web of Linked Data

* a global database
* Designed for machines first, humans later
* Primary objects are things (or descriptions of things)
* Expresses links between things
* Degree of structure in (descriptions of) things is high
* Semantics of content and links explicit

![The Semantic Web Compared To The Traditional Web @SemWeb_TradWeb_en_beck_2015]
(https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/The_Semantic_Web_Comp
ared_To_The_Traditional_Web.svg/1024px-
The_Semantic_Web_Compared_To_The_Traditional_Web.svg.png)

\newpage

# Linked Data

a way of publishing data on the Web that:

* encourages reuse
* reduces redundancy
* maximises its (real and potential) inter-connectedness
* enables network effects to add value to data


## Why publish Linked Data

* Ease of discovery
* Ease of consumption
        *  standards-based data sharing
* Reduced redundancy
* Added value
        * build ecosystems around your data/content

![The Linked Open Data cloud in 2014 (@schmachtenberg_linking_2014)](http://lod-
cloud.net/versions/2014-08-30/lod-cloud_colored.png)

\newpage

# Linked Data Basics

## [Four rules for Linked Data from Tim Berners
Lee](https://www.w3.org/DesignIssues/LinkedData.html)

1. Use URIs as names for things
1. Use HTTP URIs so that people can look up those names.
1. When someone looks up a URI, provide useful information, using the standards
(RDF*, SPARQL)
1. Include links to other URIs, so that they can discover more things.

\newpage

# The [Resource Description
Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF)
data model

RDF stores data as *triples* in the following manner:

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/12
/SubjectPredicateObject-GraphRDF.svg/640px-SubjectPredicateObject-
GraphRDF.svg.png)

This is a [graph model](https://en.wikipedia.org/wiki/Graph_(abstract_data_type)
that consists of nodes (subject and object)) and edges (predicate).

\newpage

## Data expressed as RDF

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6b/AntAsData.svg
/1024px-AntAsData.svg.png)

\newpage

## Data expressed as RDF Linked Data

![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/ba/AntAsLinkedData.sv
g/1024px-AntAsLinkedData.svg.png)

\newpage

## [RDF notation](https://en.wikipedia.org/wiki/Resource_Description_Framework)

RDF can be represented in different ways - each of which are interoperable. For
example:

* RDF/XML,
* Notation-3 (N3),
* Turtle (.ttl),
* N-Triples,
* RDFa,
* RDF/JSON

Each represent *subject, predicate, object* triples in different ways


\newpage

## One step beyond.... Linked Open Data

### [Is your Linked Open Data 5
star](https://www.w3.org/DesignIssues/LinkedData.html)

```
★       Available on the web (whatever format) but with an open licence, to be
Open Data
★★      Available as machine-readable structured data (e.g. excel instead of
image scan of a table)
★★★     as (2) plus non-proprietary format (e.g. CSV instead of excel)
★★★★    All the above plus, Use open standards from W3C (RDF and SPARQL) to
identify things, so that people can point at your stuff
★★★★★   All the above, plus: Link your data to other people’s data to provide
context
```

![Is your data 5
star](https://www.w3.org/DesignIssues/diagrams/lod/597992118v2_350x350_Back.jpg)

\newpage

# The Supporting Semantic Web Stack

![The semantic Web Stack](https://upload.wikimedia.org/wikipedia/commons/thumb/f
/f7/Semantic_web_stack.svg/768px-Semantic_web_stack.svg.png)

\newpage

## It's about re-use

### Vocabularies

The glue that joins concepts together.

A concept shared is a link gained. By re-using concepts it makes it easier to
understand what your data means and where and how it should be re-used.


```python
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/', width=1000, height=700)
```

\newpage

## It's about re-use

### Ontology

> An ontology is a shared formal explicit specialisation of a conceptualisation

![Technology used in Ontology definition(@SemWebOverview_en_beck_2012)](https://
upload.wikimedia.org/wikipedia/commons/thumb/c/cb/SemWebOverview.svg/1024px-
SemWebOverview.svg.png)

\newpage

### Ontology

* The term originated from a philosophy
        * which deals with the nature and organization of reality
* It tries to answer the questions:
        * What is being?
        * What are the features common to all beings?
        * How should things be classified?

### Ontology

> An ontology is a shared formal explicit specialisation of a conceptualisation

After Agarwal -(@agarwal_ontological_2005):

* *conceptualisation* is identifying relevant abstracted concepts of a phenomena
suited to a specific domain
* *explicit* means that the concepts are explicitly defined
* *formal* refers to the fact that the ontology should be machine-readable
* *shared* refers to notion that on ontology captures consensual knowledge

\newpage

### Ontology Example

* A ‘Carnivore’ is a concept whose members are exactly those animals who eat
only meat
* A ‘Bear’ is a concept whose members are a kind of ‘Carnivore’
* A ‘Cub’ is a concept whose members are exactly those ‘Bear’ whose age is less
than one year
* A Panda is a individual of a ‘Bear’

We can use these concepts to infer new information from facts.


For example: from the fact 'Ching Ching' is a newborn Panda we know:

```
'Ching Ching' is a Panda.
'Ching Ching' is a newborn.
```

We can infer:

```
'Ching Ching' is a Bear.
'Ching Ching' is a Carnivore.  ????
'Ching Ching' eats only meat.  ????
```

If we had other logic that told us that 'newborn' is the same as saying less
than one year then we can also infer

```
'Ching Ching' is a Cub.
```

In an ontology/RDF you can say *Anything about Anything*. Whilst carnivore is a
generally useful concept about *bears* it is not *specifically* useful when
considering *pandas*. **The domain of application is clearly important.**

\newpage

## [SPARQL](https://en.wikipedia.org/wiki/SPARQL) the SQL of the semantic web

Find me the capital of all countries in Africa:

```
PREFIX abc: <nul://sparql/exampleOntology#> .
SELECT ?capital ?country
WHERE {
  ?x abc:cityname ?capital ;
     abc:isCapitalOf ?y.
  ?y abc:countryname ?country ;
     abc:isInContinent abc:Africa.
}
```

There is a thing ('x') against which the following concepts exist:

* 'abc:cityname' (the name of a city: stored in the variable 'capital')
* 'abc:isCapitalOf' (the concept for which the city is capital: stored in the
variable 'y')

The 'concept for which the city is capital' (stored in variable 'y') must also
have the following concepts:

* 'abc:countryname' (the name of a country: stored in the variable 'country')
* 'abc:isInContinent' abc:Africa (isInContinent of the the individual Africa')

\newpage

## [GeoSPARQL](http://www.opengeospatial.org/projects/groups/geosparqlswg) the
SQL of the spatial semantic web

An OGC standard

```
SELECT ?f
WHERE { ?f my:hasPointGeometry ?fGeom .
?fGeom ogc:asWKT ?fWKT .
FILTER (ogcf:relate(?fWKT,
“<http://www.opengis.net/def/crs/OGC/1.3/CRS84>
Polygon ((-83.5 34.0, -83.5 34.3, -83.1 34.3,
-83.1 34.0, -83.5 34.0))”^^ogc:WKTLiteral,
ogc:within))
}
```

```python
from IPython.display import IFrame
IFrame('http://www.opengeospatial.org/projects/groups/geosparqlswg', width=1000, height=700)
```

# Linked Data and Geo



\newpage

## GeoSPARQL employs spatial calculus

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/Region_Connection_
Calculus_8_Relations_and_Open_Geospatial_Consortium_relations.svg/1024px-Region_
Connection_Calculus_8_Relations_and_Open_Geospatial_Consortium_relations.svg.png
)

\newpage

# Querying Linked Data in the wild

## The Ordnance Survey

A URI for every place in the UK


```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/doc/50kGazetteer/177276', width=1000, height=700)
```

\newpage

```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/id/postcodeunit/NG72QL', width=1000, height=700)
```

\newpage

```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/', width=1000, height=700)
```

\newpage

```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/ontology/', width=1000, height=700)
```

\newpage

```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/datasets/code-point-open/explorer/sparql', width=1000, height=700)
```

\newpage

## Open Street Map



```python
from IPython.display import IFrame
IFrame('http://linkedgeodata.org/About', width=1000, height=700)
```

\newpage

```python
from IPython.display import IFrame
IFrame('http://browser.linkedgeodata.org/', width=1000, height=700)


```

\newpage

## Geonames


```python
from IPython.display import IFrame
IFrame('http://www.geonames.org/ontology/documentation.html', width=1000, height=700)


```

\newpage

```python
from IPython.display import IFrame
IFrame('http://www.geonames.org/maps/google_52.94_358.8.html', width=1000, height=700)


```

\newpage

```python
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/vocabs/gn', width=1000, height=700)
```

\newpage

# Geo Vocabularies

```python
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/vocabs/?q=geo+space+address+geonames+os+spatial', width=1000, height=700)
```

\newpage

# Conclusions

* Technical interoperability is only one part of the problem
* Open data will become increasingly important as governments and other groups
release resources under clear licences
    * Licences are a barrier to re-use
* Data shows its true value when combined with other data sources – linked data
creates an opportunity
* Usability: common data model and reference of common URIs (for example,
postcodes) allows for easy data aggregation and integration.
* Shift in focus from cartography and geometries to ‘things’ and the
relationships between them.
* Spatial no longer special – part of the bigger information world....
* location is a very important information hub and provides a key underpinning
reference framework which brings many datasets together and provides important
context.

\newpage

# Geo reasoning example (if time)

Geo example:

```
Leeds is a city.

Yorkshire is a county.

Sheffield is a city.

Lancaster is a city.

Lancashire is a county.

Lancaster has a port.

What is Leeds?

Leeds isIn Yorkshire.

Sheffield isIn Yorkshire.

Lancaster isIn Lancashire.

What isIn Yorkshire?

If X isIn Y then Y contains X.

What contains Leeds?

Yorkshire borders Lancashire.

If X borders Y then Y borders X.

What borders Lancashire?

Yorkshire isIn UnitedKingdom.

Lancashire isIn UnitedKingdom.

#Transitivity

If X isIn Y and Y isIn Z then X isIn Z.

If X contains Y and Y contains Z then X contains Z


```

using proper isIn


```
Leeds is a city.

Yorkshire is a county.

Sheffield is a city.

Lancaster is a city.

Lancashire is a county.

Lancaster has a port.

What is Leeds?

Leeds is spatiallyWithin Yorkshire.

Sheffield is spatiallyWithin Yorkshire.

Lancaster is spatiallyWithin Lancashire.

What is spatiallyWithin Yorkshire?

If X is spatiallyWithin Y then Y spatiallyContains X.

What spatiallyContains Leeds?

Yorkshire borders Lancashire.

If X borders Y then Y borders X.

What borders Lancashire?

Yorkshire is spatiallyWithin UnitedKingdom.

Lancashire is spatiallyWithin UnitedKingdom.

#Transitivity

If X is spatiallyWithin Y and Y is spatiallyWithin Z then X is spatiallyWithin
Z.

If X spatiallyContains Y and Y spatiallyContains Z then X spatiallyContains Z

What is spatiallyWithin UnitedKingdom?
```

Adding more......

```
Pudsey is spatiallyWithin Leeds.

Kirkstall is spatiallyWithin Leeds.

Meanwood is spatiallyWithin Leeds.

Roundhay is spatiallyWithin Leeds.

Scarcroft is spatiallyWithin Leeds.

```

and more

```


UnitedKingdom isPartOf Europe.

UnitedKingdom is a country.

If X isPartOf Y and X spatiallyContains Z then Z isPartOf Y.

What isPartOf Europe?

```

```python
and more

```

If X spatiallyContains Y and X is a city then Y is a place and Y is a cityPart.


Every city is a place.

What is a place.

```
```

```python
and more

```
UK isPartOf Europe.

UK is sameAs UnitedKingdom.

If X has a port then X borders Water.

What borders Water?
```
```

# Questions

In terms of discussion I'm interested in how these issues affect you.........

![Processing transparency between open and closed systems](https://upload.wikime
dia.org/wikipedia/commons/thumb/d/d5/Processing_transparency_between_open_and_cl
osed_systems.svg/630px-
Processing_transparency_between_open_and_closed_systems.svg.png)

\newpage

# References
