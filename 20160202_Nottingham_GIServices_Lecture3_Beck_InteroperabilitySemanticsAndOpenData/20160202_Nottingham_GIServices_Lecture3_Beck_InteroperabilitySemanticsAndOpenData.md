
![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/InteroperabilitySemanticsAndOpenData.png)


Go down for licence and other metadata about this presentation

\newpage

# Preamble

## Licence

Unless stated otherwise all content is released under a [CC0]+BY licence. I'd appreciate it if you reference this but it is not necessary.

![](https://dl.dropboxusercontent.com/u/393477/SharedPresentations/Shared_HTML5/Images/CC_BY.png)

\newpage

## Using Ipython for presentations

A short video showing how to use Ipython for presentations


```python
from IPython.display import YouTubeVideo
YouTubeVideo('F4rFuIb1Ie4')
```





        <iframe
            width="400"
            height="300"
            src="https://www.youtube.com/embed/F4rFuIb1Ie4"
            frameborder="0"
            allowfullscreen
        ></iframe>
        




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

    ipython nbconvert --to markdown 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb





    0



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

    Installed watermark.py. To use it, type:
      %load_ext watermark


    /home/arb/LocalInstalls/anaconda3/lib/python3.5/site-packages/IPython/core/magics/extension.py:47: UserWarning: %install_ext` is deprecated, please distribute your extension(s)as a python packages.
      "as a python packages.", UserWarning)



```python
%watermark -a "Anthony Beck"  -d -v -m -g
```

    Anthony Beck 24/01/2016 
    
    CPython 3.5.1
    IPython 4.0.2
    
    compiler   : GCC 4.4.7 20120313 (Red Hat 4.4.7-1)
    system     : Linux
    release    : 3.19.0-32-generic
    machine    : x86_64
    processor  : x86_64
    CPU cores  : 4
    interpreter: 64bit
    Git hash   : 



```python
#List of installed conda packages
!conda list
```

    # packages in environment at /home/arb/LocalInstalls/anaconda3:
    #
    _license                  1.1                      py35_1    defaults
    abstract-rendering        0.5.1               np110py35_0    defaults
    accelerate                2.0                np110py35_p0    defaults
    accelerate_cudalib        2.0                           0    defaults
    affine                    1.2.0                    py35_0    https://conda.binstar.org/ioos/linux-64/affine-1.2.0-py35_0.tar.bz2
    alabaster                 0.7.6                    py35_0    defaults
    anaconda                  2.4.1               np110py35_0    defaults
    anaconda-client           1.2.1                    py35_0    defaults
    argcomplete               1.0.0                    py35_1    defaults
    astropy                   1.1.1               np110py35_0    defaults
    babel                     2.1.1                    py35_0    defaults
    basemap                   1.0.7               np110py35_0    defaults
    beautifulsoup4            4.4.1                    py35_0    defaults
    bitarray                  0.8.1                    py35_0    defaults
    blaze                     0.9.0                     <pip>
    blaze-core                0.9.0                    py35_0    defaults
    bokeh                     0.11.0                   py35_1    defaults
    boto                      2.38.0                   py35_0    defaults
    bottleneck                1.0.0               np110py35_0    defaults
    cffi                      1.2.1                    py35_0    defaults
    click                     4.1                      py35_0    defaults
    click-plugins             1.0.2                    py35_0    https://conda.binstar.org/ioos/linux-64/click-plugins-1.0.2-py35_0.tar.bz2
    cligj                     0.2.0                    py35_0    defaults
    clyent                    1.2.0                    py35_0    defaults
    colorama                  0.3.3                    py35_0    defaults
    colorlover                0.2.1                     <pip>
    conda                     3.19.0                   py35_0    defaults
    conda-build               1.18.2                   py35_0    defaults
    conda-env                 2.4.5                    py35_0    defaults
    configobj                 5.0.6                    py35_0    defaults
    cryptography              1.0.2                    py35_0    defaults
    cudatoolkit               7.0                           1    defaults
    cufflinks                 0.7.1                     <pip>
    curl                      7.43.0                        1    defaults
    cycler                    0.9.0                    py35_0    defaults
    cython                    0.23.4                   py35_0    defaults
    cytoolz                   0.7.4                    py35_0    defaults
    datashape                 0.5.0                    py35_0    defaults
    decorator                 4.0.6                    py35_0    defaults
    descartes                 1.0.1                    py35_0    https://conda.binstar.org/ioos/linux-64/descartes-1.0.1-py35_0.tar.bz2
    docutils                  0.12                     py35_0    defaults
    dynd                      9b63882                   <pip>
    dynd-python               0.7.0                    py35_0    defaults
    et-xmlfile                1.0.1                     <pip>
    et_xmlfile                1.0.1                    py35_0    defaults
    fastcache                 1.0.2                    py35_0    defaults
    fiona                     1.6.0               np110py35_0    defaults
    flask                     0.10.1                   py35_1    defaults
    fontconfig                2.11.1                        5    defaults
    freetype                  2.5.5                         0    defaults
    funcsigs                  0.4                      py35_0    defaults
    gdal                      2.0.0                    py35_1    defaults
    geos                      3.3.3                         0    defaults
    greenlet                  0.4.9                    py35_0    defaults
    h5py                      2.5.0               np110py35_4    defaults
    hdf4                      4.2.11                        0    defaults
    hdf5                      1.8.15.1                      2    defaults
    html5lib                  0.9999999                 <pip>
    idna                      2.0                      py35_0    defaults
    iopro                     1.7.2              np110py35_p0    defaults
    ipykernel                 4.2.2                    py35_0    defaults
    ipython                   4.0.2                    py35_0    defaults
    ipython-genutils          0.1.0                     <pip>
    ipython-notebook          4.0.4                    py35_0    defaults
    ipython-qtconsole         4.0.1                    py35_0    defaults
    ipython_genutils          0.1.0                    py35_0    defaults
    ipywidgets                4.1.1                    py35_0    defaults
    itsdangerous              0.24                     py35_0    defaults
    jbig                      2.1                           0    defaults
    jdcal                     1.2                      py35_0    defaults
    jedi                      0.9.0                    py35_0    defaults
    jinja2                    2.8                      py35_0    defaults
    jpeg                      8d                            0    defaults
    jsonschema                2.4.0                    py35_0    defaults
    jupyter                   1.0.0                    py35_1    defaults
    jupyter-client            4.1.1                     <pip>
    jupyter-console           4.1.0                     <pip>
    jupyter-core              4.0.6                     <pip>
    jupyter_client            4.1.1                    py35_0    defaults
    jupyter_console           4.1.0                    py35_0    defaults
    jupyter_core              4.0.6                    py35_0    defaults
    kealib                    1.4.5                         0    defaults
    krb5                      1.13.2                        0    defaults
    libdynd                   0.7.0                         0    defaults
    libffi                    3.0.13                        0    defaults
    libgdal                   2.0.0                         1    defaults
    libgfortran               1.0                           0    defaults
    libnetcdf                 4.3.3.1                       1    defaults
    libpng                    1.6.17                        0    defaults
    libsodium                 1.0.3                         0    defaults
    libtiff                   4.0.6                         1    defaults
    libxml2                   2.9.2                         0    defaults
    libxslt                   1.1.28                        0    defaults
    llvmlite                  0.8.0                    py35_0    defaults
    lxml                      3.5.0                    py35_0    defaults
    markupsafe                0.23                     py35_0    defaults
    matplotlib                1.5.1               np110py35_0    defaults
    mistune                   0.7.1                    py35_0    defaults
    mkl                       11.1               np110py35_p1    defaults
    mkl-rt                    11.1                         p0    defaults
    mkl-service               1.1.0                   py35_p0    defaults
    mock                      1.3.0                    py35_0    defaults
    multipledispatch          0.4.8                    py35_0    defaults
    nbconvert                 4.1.0                    py35_0    defaults
    nbformat                  4.0.1                    py35_0    defaults
    networkx                  1.10                     py35_0    defaults
    nltk                      3.1                      py35_0    defaults
    nose                      1.3.7                    py35_0    defaults
    notebook                  4.1.0                    py35_0    defaults
    numba                     0.22.1              np110py35_0    defaults
    numbapro                  0.22.1                  py35_p0    defaults
    numexpr                   2.4.4              np110py35_p0  [mkl]  defaults
    numpy                     1.10.2                  py35_p0  [mkl]  defaults
    odo                       0.4.0                    py35_0    defaults
    openblas                  0.2.14                        3    defaults
    openjpeg                  2.1.0                         0    https://conda.binstar.org/ioos/linux-64/openjpeg-2.1.0-0.tar.bz2
    openpyxl                  2.3.2                    py35_0    defaults
    openssl                   1.0.2e                        0    defaults
    owslib                    0.10.3                   py35_0    https://conda.binstar.org/ioos/linux-64/owslib-0.10.3-py35_0.tar.bz2
    pandas                    0.17.1              np110py35_0    defaults
    patchelf                  0.8                           0    defaults
    path.py                   8.1.2                    py35_1    defaults
    patsy                     0.4.0               np110py35_0    defaults
    pbr                       1.3.0                    py35_0    defaults
    pep8                      1.6.2                    py35_0    defaults
    pexpect                   3.3                      py35_0    defaults
    pickleshare               0.5                      py35_0    defaults
    pillow                    3.1.0                    py35_0    defaults
    pip                       7.1.2                    py35_0    defaults
    plotly                    1.9.5                     <pip>
    ply                       3.8                      py35_0    defaults
    postgresql                9.1.4                         0    defaults
    proj.4                    4.9.1                         1    https://conda.binstar.org/ioos/linux-64/proj.4-4.9.1-1.tar.bz2
    proj4                     4.9.1                         1    SciTools
    psutil                    3.3.0                    py35_0    defaults
    ptyprocess                0.5                      py35_0    defaults
    py                        1.4.30                   py35_0    defaults
    pyasn1                    0.1.9                    py35_0    defaults
    pycosat                   0.6.1                    py35_0    defaults
    pycparser                 2.14                     py35_0    defaults
    pycrypto                  2.6.1                    py35_0    defaults
    pycurl                    7.19.5.1                 py35_2    defaults
    pyepsg                    0.2.0                    py35_0    SciTools
    pyflakes                  1.0.0                    py35_0    defaults
    pygments                  2.0.2                    py35_0    defaults
    pyodbc                    3.0.10                   py35_0    defaults
    pyopenssl                 0.15.1                   py35_1    defaults
    pyparsing                 2.0.3                    py35_0    defaults
    pyproj                    1.9.4                    py35_1    defaults
    pyqt                      4.11.4                   py35_1    defaults
    pyshp                     1.2.3                    py35_0    https://conda.binstar.org/ioos/linux-64/pyshp-1.2.3-py35_0.tar.bz2
    pytables                  3.2.2               np110py35_0    defaults
    pytest                    2.8.1                    py35_0    defaults
    python                    3.5.1                         0    defaults
    python-dateutil           2.4.2                    py35_0    defaults
    pytz                      2015.7                   py35_0    defaults
    pyyaml                    3.11                     py35_1    defaults
    pyzmq                     15.2.0                   py35_0    defaults
    qt                        4.8.7                         1    defaults
    qtconsole                 4.1.1                    py35_0    defaults
    rasterio                  0.25.0              np110py35_0    defaults
    readline                  6.2                           2    defaults
    redis                     2.6.9                         0    defaults
    redis-py                  2.10.3                   py35_0    defaults
    requests                  2.9.1                    py35_0    defaults
    rope                      0.9.4                    py35_1    defaults
    rope-py3k-0.9.4           1                         <pip>
    scikit-image              0.11.3              np110py35_0    defaults
    scikit-learn              0.17               np110py35_p1  [mkl]  defaults
    scipy                     0.16.1             np110py35_p0  [mkl]  defaults
    seaborn                   0.6.0               np110py35_0    defaults
    setuptools                19.2                     py35_0    defaults
    shapely                   1.5.11                   py35_0    defaults
    simplegeneric             0.8.1                    py35_0    defaults
    simplejson                3.8.1                     <pip>
    sip                       4.16.9                   py35_0    defaults
    six                       1.10.0                   py35_0    defaults
    snowballstemmer           1.2.0                    py35_0    defaults
    snuggs                    1.3.1               np110py35_0    defaults
    sockjs-tornado            1.0.1                    py35_0    defaults
    sphinx                    1.3.1                    py35_0    defaults
    sphinx-rtd-theme          0.1.7                     <pip>
    sphinx_rtd_theme          0.1.7                    py35_0    defaults
    spyder                    2.3.8                    py35_0    defaults
    spyder-app                2.3.8                    py35_0    defaults
    sqlalchemy                1.0.11                   py35_0    defaults
    sqlite                    3.9.2                         0    defaults
    statsmodels               0.6.1               np110py35_0    defaults
    sympy                     0.7.6.1                  py35_0    defaults
    tables                    3.2.2                     <pip>
    terminado                 0.5                      py35_1    defaults
    theano                    0.7.0               np110py35_0    defaults
    tk                        8.5.18                        0    defaults
    toolz                     0.7.4                    py35_0    defaults
    tornado                   4.3                      py35_0    defaults
    traitlets                 4.1.0                    py35_0    defaults
    ujson                     1.33                     py35_0    defaults
    unicodecsv                0.14.1                   py35_0    defaults
    unixodbc                  2.3.1                         1    defaults
    util-linux                2.21                          0    defaults
    werkzeug                  0.11.3                   py35_0    defaults
    wheel                     0.26.0                   py35_1    defaults
    xerces-c                  3.1.2                         0    defaults
    xlrd                      0.9.4                    py35_0    defaults
    xlsxwriter                0.8.2                    py35_0    defaults
    xlwt                      1.0.0                    py35_0    defaults
    xz                        5.0.5                         0    defaults
    yaml                      0.1.6                         0    defaults
    zeromq                    4.1.3                         0    defaults
    zlib                      1.2.8                         0    defaults



```python
#List of installed pip packages
!pip list
```

    abstract-rendering (0.5.1)
    accelerate (2.0.0)
    affine (1.2.0)
    alabaster (0.7.6)
    anaconda-client (1.2.1)
    argcomplete (1.0.0)
    astropy (1.1.1)
    Babel (2.1.1)
    basemap (1.0.7)
    beautifulsoup4 (4.4.1)
    bitarray (0.8.1)
    blaze (0.9.0)
    bokeh (0.11.0)
    boto (2.38.0)
    Bottleneck (1.0.0)
    cffi (1.2.1)
    click (4.1)
    click-plugins (1.0.2)
    cligj (0.2.0)
    clyent (1.2.0)
    colorama (0.3.3)
    colorlover (0.2.1)
    conda (3.19.0)
    conda-build (1.18.2)
    conda-env (2.4.5)
    configobj (5.0.6)
    cryptography (0.9.3)
    cufflinks (0.7.1)
    cycler (0.9.0)
    Cython (0.23.4)
    cytoolz (0.7.4)
    datashape (0.5.0)
    decorator (4.0.6)
    descartes (1.0.1)
    docutils (0.12)
    dynd (9b63882)
    et-xmlfile (1.0.1)
    fastcache (1.0.2)
    Fiona (1.6.0)
    Flask (0.10.1)
    funcsigs (0.4)
    GDAL (2.0.0)
    greenlet (0.4.9)
    h5py (2.5.0)
    html5lib (0.9999999)
    idna (2.0)
    iopro (1.7.2)
    ipykernel (4.2.2)
    ipython (4.0.2)
    ipython-genutils (0.1.0)
    ipywidgets (4.1.1)
    itsdangerous (0.24)
    jdcal (1.2)
    jedi (0.9.0)
    Jinja2 (2.8)
    jsonschema (2.4.0)
    jupyter (1.0.0)
    jupyter-client (4.1.1)
    jupyter-console (4.1.0)
    jupyter-core (4.0.6)
    llvmlite (0.8.0)
    lxml (3.5.0)
    MarkupSafe (0.23)
    matplotlib (1.5.1)
    mistune (0.7.1)
    mock (1.3.0)
    multipledispatch (0.4.8)
    nbconvert (4.1.0)
    nbformat (4.0.1)
    networkx (1.10)
    nltk (3.1)
    nose (1.3.7)
    notebook (4.1.0)
    numba (0.22.1)
    numbapro (0.22.1)
    numexpr (2.4.4)
    numpy (1.10.2)
    odo (0.4.0)
    openpyxl (2.3.2)
    OWSLib (0.10.3)
    pandas (0.17.1)
    path.py (0.0.0)
    patsy (0.4.0)
    pbr (1.3.0)
    pep8 (1.6.2)
    pexpect (3.3)
    pickleshare (0.5)
    Pillow (3.1.0)
    pip (8.0.2)
    plotly (1.9.5)
    ply (3.8)
    psutil (3.3.0)
    ptyprocess (0.5)
    py (1.4.30)
    pyasn1 (0.1.9)
    pycosat (0.6.1)
    pycparser (2.14)
    pycrypto (2.6.1)
    pycurl (7.19.5.1)
    pyepsg (0.2.0)
    pyflakes (1.0.0)
    Pygments (2.0.2)
    pyodbc (3.0.10)
    pyOpenSSL (0.15.1)
    pyparsing (2.0.3)
    pyproj (1.9.4)
    pyshp (1.2.3)
    pytest (2.8.1)
    python-dateutil (2.4.2)
    pytz (2015.7)
    PyYAML (3.11)
    pyzmq (15.2.0)
    qtconsole (4.1.1)
    rasterio (0.25.0)
    redis (2.10.3)
    requests (2.9.1)
    rope-py3k (0.9.4.post1)
    scikit-image (0.11.3)
    scikit-learn (0.17)
    scipy (0.16.1)
    seaborn (0.6.0)
    setuptools (19.2)
    Shapely (1.5.11)
    simplegeneric (0.8.1)
    simplejson (3.8.1)
    six (1.10.0)
    snowballstemmer (1.2.0)
    snuggs (1.3.1)
    sockjs-tornado (1.0.1)
    Sphinx (1.3.1)
    sphinx-rtd-theme (0.1.7)
    spyder (2.3.8)
    SQLAlchemy (1.0.11)
    statsmodels (0.6.1)
    sympy (0.7.6.1)
    tables (3.2.2)
    terminado (0.5)
    Theano (0.7.0)
    toolz (0.7.4)
    tornado (4.3)
    traitlets (4.1.0)
    ujson (1.33)
    unicodecsv (0.14.1)
    Werkzeug (0.11.3)
    wheel (0.26.0)
    xlrd (0.9.4)
    XlsxWriter (0.8.2)
    xlwt (1.0.0)


## Running dynamic presentations

You need to install the [RISE Ipython Library](https://github.com/damianavila/RISE) from [Damián Avila](https://github.com/damianavila) for dynamic presentations

To convert and run this as a static presentation run the following command:


```python
# Notes don't show in a python3 environment

!ipython nbconvert 2016_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb --to slides --post serve


```

    [NbConvertApp] Converting notebook 2016_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb to slides
    [NbConvertApp] Writing 292732 bytes to 2016_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.slides.html
    [NbConvertApp] Redirecting reveal.js requests to https://cdnjs.cloudflare.com/ajax/libs/reveal.js/3.1.0
    Serving your slides at http://127.0.0.1:8000/2016_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.slides.html
    Use Control-C to stop this server
    Created new window in existing browser session.
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 0.90ms
    WARNING:tornado.access:404 GET /favicon.ico (127.0.0.1) 0.80ms


To close this instances press *control 'c'* in the *ipython notebook* terminal console

Static presentations allow the presenter to see *speakers notes* (use the 's' key)

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

    Populating the interactive namespace from numpy and matplotlib


\newpage

## About me

 

![It's all about me - details about Anthony Beck](https://dl.dropboxusercontent.com/u/393477/ImageBank/Geolytics_ARB_Banner.png)

* Honorary Research Fellow, University of Nottingham: [orcid](http://orcid.org/0000-0002-2991-811X)
* Director, Geolytics Limited - A spatial data analytics consultancy

## About this presentation

* [Available on GitHub](https://github.com/AntArch/Presentations_Github/tree/master/20151008_OpenGeo_Reuse_under_licence) - https://github.com/AntArch/Presentations_Github/
* [Fully referenced PDF](https://github.com/AntArch/Presentations_Github/blob/master/20150916_OGC_Reuse_under_licence/20151008_OpenGeo_Reuse_under_licence.pdf)


\newpage

# Contribution to GIScience learning outcomes

This presentation contributes to the following learning outcomes for this course.

1. Knowledge and Understanding:
	* Appreciate the importance of standards for Geographic Information and the role of the Open Geospatial Consortium.
	* Understand the term 'interoperability'.
	* Appreciate the different models for database design.
	* Understand the basis of Linked Data.
	* Find UK government open data and understand some of the complexities in the use of this data.
	* Appreciate the data issues involved in managing large distributed databases, Location-Based Services and the emergence of real-time data gathering through the 'Sensor-Web'.
	* Understand the different models for creating international Spatial Data Infrastructures.
1. Intellectual Skills:
	* Evaluate the role of standards and professional bodies in GIS.
	* Articulate the meaning and importance of interoperability, semantics and ontologies.
	* Assess the technical and organisational issues which come into play when attempting to design large distributed geographic databases aimed at supporting 'real-world' problems.
    


# A potted history of mapping

## In the beginning was the geoword


and the word was ***cartography***


![The lens of cartography @TheLensOfCartography_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/TheLensOfCartography.svg/1024px-TheLensOfCartography.svg.png)


\newpage

![A static map (public domain) encapsulating spatial knowledge in a portable manner](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/Claudius_Ptolemy-_The_World.jpg/1024px-Claudius_Ptolemy-_The_World.jpg)

* Cartography was king. 
* Static representations of spatial knowledge with the cartographer deciding what to represent. 
    * Hence, maps are domain specific knowledge repositories for spatial data

\newpage

# And then there was data .........




![Data @Data_types_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Data_types_-_en.svg/576px-Data_types_-_en.svg.png)

\newpage

![But the data was siloed (restricted use)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/TheEndOfThe20thCentury.png)

Restrictive data

\newpage

![The implications of a landscape of silo-ed data @IslandsOfData_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Islands_Of_Data.svg/1017px-Islands_Of_Data.svg.png)

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





        <iframe
            width="400"
            height="300"
            src="https://www.youtube.com/embed/xew6qI-6wNk"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

# INSPIRE principles

* Data should be collected only once and kept where it can be maintained most effectively
* It should be possible to combine seamless spatial information from different sources across Europe and share it with many users and applications
* It should be possible for information collected at one level/scale to be shared with all levels/scales; detailed for thorough investigations, general for strategic purposes
* Geoinformation needed for good governance at all levels should be readily and transparently available
* Easy to find what geoinformation is available, how it can be used to meet a particular need, and under which conditions it can be acquired and used

\newpage

![Concerted efforts to de-silo data and make data interoperable (restricted use)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/TheCatalyst.png)

Making data interoperable and open

\newpage

# Interoperability

> is a property of a product or system, whose interfaces are completely understood, to work with other products or systems, present or future, without any restricted access or implementation.

@wikipedia_interoperability_2016




[The Defense domain are a bit more explicit......](http://www.dau.mil/pubscats/atl%20docs/jan-feb/watson_jan-feb10.pdf)

> As defined by DoD policy, interoperability is the ability of systems, units, or forces to provide data, information, material, and services to, and accept the same from, other systems, units, or forces; and to use the data, information, material, and services so exchanged to enable them to operate effectively together. IT and NSS interoperability includes both the technical exchange of information and the end-to-end operational effectiveness of that exchanged information as required for mission accomplishment. Interoperability is more than just information exchange; it includes systems, processes, procedures, organizations, and missions over the life cycle and must be balanced with information assurance.

@watson_joint_2010

\newpage

# Technical interoperability - levelling the field

![Interoperable integration of spatial data - the technological issues @TechnicalInteroperableIntegrationOfSpatialData_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/TechnicalInteroperableIntegrationOfSpatialData.svg/1024px-TechnicalInteroperableIntegrationOfSpatialData.svg.png)

\newpage

# Syntactic Heterogeneity

> the difference in data format. The same **logical model** can be represented in a range of different **physical models** (for example ESRI shape file or Geography Mark-up Language (GML)).

This mismatch between underlying data models implies that the same information could be represented differently in different organisations. 

The most profound difference is in the storage paradigm: 

* relational, 
* object orientated or
* hybrids.

@beck_uk_2008, @bishr_overcoming_1998


\newpage

# Semantic Heterogeneity

> Semantic heterogeneity refers to differences in naming conventions and conceptual groupings.

This can be subdivided into **naming** and **cognitive** heterogeneities. 

* Naming (synonym) mismatch arises when semantically identical data items are named differently. 
* Cognitive (homonym) mismatch arises when semantically different data items are named identically.
    * Cognitive semantics can be subtle, reflecting the domain of discourse.

@beck_uk_2008, @bishr_overcoming_1998


\newpage

# Schematic Heterogeneity

> refers to the differences in data model between organisations modelling the same concepts. 

This reflects each organisation’s abstracted view of their business and physical assets. Hence, different hierarchical and classification concepts are adopted by each organisation to refer to identical or similar real world objects.

@beck_uk_2008, @bishr_overcoming_1998


\newpage

# The role of the OGC (a geospatial standards body)


* To serve as a global forum for the development, promotion and harmonization of *open and freely available* **geospatial standards**
* To achieve the full societal, economic and scientific benefits of integrating electronic location resources into commercial and institutional processes worldwide. 

![The OGC Logo](http://www2.isprs.org/tl_files/isprs/comm2/symposium/Documents/OGC_logo.png)



\newpage

# The role of the OGC (a geospatial standards body)

OGC’s Open Standards are:

* Freely and publicly available
* Non discriminatory
* No license fees
* Vendor neutral
* Data neutral
* Adopted in a formal, member based consensus process

OGC’s Open Standards are submitted to other industry and National Standards Development Organisations in the vertical area and to global organisations like ISO for standard branding. 

\newpage

# OGC Technologies

* The OGC publish standards that have been agreed by OGC members
* Current standards can be found at: [http://www.opengeospatial.org/standards](http://www.opengeospatial.org/standards)
* These are implementation standards
	* written for a more technical audience and detail the interface structure between software components
* Predicated on abstract specifications
	* the conceptual foundation for most OGC standards development activities
	* [http://www.opengeospatial.org/specs/?page=abstract](http://www.opengeospatial.org/specs/?page=abstract)


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
* [GML – The Geography Markup Language](http://www.opengeospatial.org/standards/gml)
	* Used as an interoperable standard for transmitting geographic data (2D, 3D, topology, etc.)
	* Versions 2.1.x and 3.2.1 are most relevant

\newpage

# Other OGC standards


```python
from IPython.display import IFrame
IFrame('http://www.opengeospatial.org/standards', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://www.opengeospatial.org/standards"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

# Interoperability in action

![The use of OGC standards in an interoperable multi-data delivery environment @GeoServerGeoNetworkWithWebApp2013](https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/GeoServer_GeoNetwork_with_web_app.svg/877px-GeoServer_GeoNetwork_with_web_app.svg.png)

\newpage

# What did technical interoperability facilitate

![From Map to Model The changing paradigm of map creation from cartography to data driven visualization @FromMapToModel_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/FromMapToModel.svg/1024px-FromMapToModel.svg.png)

From Map to Model The changing paradigm of map creation from cartography to data driven visualization

\newpage

![A new working paradigm (public domain)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/ANewWorkingParadigm.png)

\newpage

# The world was a happy place.......

Our data was interoperable!

![But time moved on @NonsymmetricVelocity_en_cleonis_2006](https://upload.wikimedia.org/wikipedia/commons/7/72/Nonsymmetric_velocity_time_dilation.gif)


\newpage

# Then ....... along came **open data**

![open data word cloud of Anthony Beck](https://dl.dropboxusercontent.com/u/393477/SharedPresentations/Shared_HTML5/Images/ARB_WordleCloud.png)

\newpage

# The Open landscape integrates **formal** and **informal** data

![Local To Global integration of data to create multiple generic products @Local_To_Global_integration_of_data_to_create_multiple_generic_products_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Local_To_Global_integration_of_data_to_create_multiple_generic_products.svg/1024px-Local_To_Global_integration_of_data_to_create_multiple_generic_products.svg.png)

\newpage

![Cartography is no longer key. Spatial mapping is now about the the formal and informal data stack. Elements such as provenance, credibility are much more important for use and re-use of this data. @CartographyNoLongerKing_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/CartographyNoLongerKing.svg/1024px-CartographyNoLongerKing.svg.png)

\newpage

# Background  - originally a grass roots (community) movement..

![The Open Knowledge Foundation (@Open_Knowledge_logo), Open Street Map (@Openstreetmap_logo), Wikipedia (@Wikipedia-logo-v2-en) and OSGeo](https://dl.dropboxusercontent.com/u/393477/ImageBank/Open_logos.png)


Open access to knowledge gained significant momementum with the increased uptake of the World Wide Web. This is particularly seen in initiatives like [Wikipedia](https://en.wikipedia.org) (established in 2001) and [Open Knowledge](https://en.wikipedia.org/wiki/Open_Knowledge) (was the Open Knowledge Foundation: established in 2004). Within the Geo community [Open Street Map ](https://en.wikipedia.org/wiki/OpenStreetMap) (also established in 2004) and the [Open Source Geospatial Foundation](https://en.wikipedia.org/wiki/Open_Source_Geospatial_Foundation) (OSGeo - established in 2006) are key initiatives that promote accessible data and software resources respectively.

Critical to this is that these were **grass roots** (community) movements that have proven to be highly disruptive to incumbent data providers, practices and policies. 

\newpage

# Open in government

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/InteroperabilitySemanticsAndOpenData.png)

The impact of these grass roots movements is seen in Open Data (dot) gov. Pioneered by leaders such as Tim Berners Lee and Nigel Shadbolt

The Shakespeare review [-@shakespeare_shakespeare_2013] indicate that the amount of government Open Data, at least in the UK, is only going to grow.
Open data has the potential to trigger a revolution in how governments think about providing services to citizens and how they measure their success: this produces societal impact.
This will require an understanding of citizen needs, behaviours, and mental models, and how to use data to improve services.

\newpage

## Valuing Open Data

![McKinsey report valuing *open data* [@mckinsey_open_2013]](https://dl.dropboxusercontent.com/u/393477/ImageBank/Mckinsey_Value_of_OpenData.png)

A [McKinsey Global Institute report examines the economic impact of Open Data](http://www.mckinsey.com/insights/business_technology/open_data_unlocking_innovation_and_performance_with_liquid_information) [@mckinsey_open_2013] and estimates that globally open data could be worth a minimum of $3 trillion annually. 

\newpage

# Open in academia

> Open inquiry is at the heart of the scientific enterprise..... Science’s powerful capacity for self-correction comes from this openness to scrutiny and challenge.

*Science as an open enterprise* [@royal_society_science_2012 p. 7].

>Science is based on building on, reusing and openly criticising the published body of scientific knowledge.

>For science to effectively function, and for society to reap the full benefits from scientific endeavours, it is crucial that science data be made open.

The Panton Principles (@murray-rust_panton_2010) which underpin **Open Science**.


The Royal Society’s report Science as an open enterprise [-@royal_society_science_2012] identifies how 21^st^ century communication technologies are changing the ways in which scientists conduct, and society engages with, science. The report recognises that ‘open’ enquiry is pivotal for the success of science, both in research and in society.

The Panton Principles pre-cursed this call with a clarion call to the academic community to open their data and start to conduct **open science**.

![@open_science_does_not_equal_open_access_2013](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Open_Science_Does_Not_Equal_Open_Access.svg/1024px-Open_Science_Does_Not_Equal_Open_Access.svg.png)

This goes beyond open access to publications (Open Access), to include access to data and other research outputs (Open Data), and the process by which data is turned into knowledge (Open Science).

## The next generation open data in academia

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/zenodo.png)

Zenodo is a **DATA REPOSITORY** which offers:

* accreditation 
* different licences 
* different exposure (private (closed), public (open) and embargoed (timestamped)) 
* DOIs 
* is free at the point of use  
* is likely to be around for a long time 
    * supported by Horizon 2020 and delivered by CERN
    


\newpage

# The underlying rationale of Open Data is: 

* unfettered access to large amounts of ‘raw’ data 
    * enables patterns of re-use and knowledge creation that were previously impossible. 
    * improves transparency and efficiency
    * encourages innovative service delivery
* introduces a range of data-mining and visualisation challenges, 
    * which require multi-disciplinary collaboration across domains
    * catalyst to research and industry
* supports the generation of new products, services and markets
* the prize for succeeding is improved knowledge-led policy and practice that transforms 
    * communities, 
    * practitioners, 
    * science and 
    * society


\newpage

# Free and Open Source Software in in Geo 


```python
from IPython.display import IFrame
IFrame('http://www.osgeo.org/', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://www.osgeo.org/"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

# So...... we have access to lots of data and software

* Formal and Informal
* Open and Proprietary




# Where are these new data products?

Data, data everywhere - but where are the new derivatives and services?


\newpage

# Non-technical interoperability issues?



![Islands of incompatibility [@IncompatibilitiesAndLicenceClauses_en_beck_2016]](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Incompatibilities_And_Licence_Clauses.svg/989px-Incompatibilities_And_Licence_Clauses.svg.png)

\newpage

\newpage

![The full stack that enables interoperable integration of spatial data @InteroperableIntegrationOfSpatialData_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/InteroperableIntegrationOfSpatialData.svg/500px-InteroperableIntegrationOfSpatialData.svg.png)

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

Social interoperability is concerned about the environment and business and human processes.

* Tools are used by people
* The social dimension of operational use is underestimated (it's difficult)
* People form complex inclusive and exclusive networks
    * These operate at many scales

[US Department of Defence researchers have advocated](http://www.dtic.mil/ndia/2009systemengr/8854WednesdayTrack8Zavin.pdf) the development of Policy, Standards, and Operational Procedures for:

* forming human networks
* human to human communications
* organization to organization communications
* human system integration
* information sharing across disparate domains:
     * DoD-Coalition-Interagency-intercommunity


\newpage

## Legal Interoperability

> Legal interoperability addresses the process of making legal rules cooperate across jurisdictions, on different subsidiary levels within a single state or between two or more states. 

(@weber_legal_2014, p. 6)

The [Research Data Alliance](https://rd-alliance.org/) state that [legal interoperability occurs among multiple datasets when](https://rd-alliance.org/group/rdacodata-legal-interoperability-ig/wiki/legal-principles-data.html):

* use conditions are clearly and readily determinable for each of the datasets,
* the legal use conditions imposed on each dataset allow creation and use of combined or derivative products, and
* users may legally access and use each dataset without seeking authorization from data rights holders on a case-by-case basis, assuming that the accumulated conditions of use for each and all of the datasets are met.

Legal interoperability also implies that the search for or tracking of licenses or other legal instruments and their compatibility with other legal conditions will occur in online environments. 

\newpage

### Licence Interoperability

A specific form of legal interoperability

\newpage

# Example of applying the semantic web to licence interoperability

![The modern data landscape (restricted)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/20151008_Re-UseUnderLicence.png)

There is a multitude of formal and informal data. 

\newpage

## What is a licence?

[Wikipedia state:](https://en.wikipedia.org/wiki/License)

> A license may be granted by a party ("licensor") to another party ("licensee") as an element of an agreement between those parties. 

> A shorthand definition of a license is "an authorization (by the licensor) to use the licensed material (by the licensee)."



![Some licences @rdflicense_2015](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/SomeLicences_FromRDFLicences.png)

Each of these data objects can be licenced in a different way. This shows some of the licences described by the RDFLicence ontology

\newpage


```python
### Export this notebook as markdown
commandLineSyntax = 'dot -Tpng FCA_ConceptAnalysis.dot > FCA_ConceptAnalysis.png'
commandLineSyntax = 'dot -Tsvg FCA_ConceptAnalysis.dot > FCA_ConceptAnalysis.svg'
print (commandLineSyntax)

os.system(commandLineSyntax)

```

![Concepts surrounding licences (derived from Formal Concept Analysis)](http://g.gravizo.com/g?
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
     o -> n -> q -> j -> i -> g -> k -> l -> e -> c -> g -> h -> j -> f -> e -> r -> g;
     r -> s;
 }
)

![Concepts surrounding licences (derived from Formal Concept Analysis)](https://dl.dropboxusercontent.com/u/393477/ImageBank/FCA_ConceptAnalysis.png)

Concepts (derived from Formal Concept Analysis) surrounding licences

\newpage

Two lead organisations have developed legal frameworks for content licensing:

* [Creative Commons (CC)](https://creativecommons.org/) and 
* [Open Data Commons (ODC)](http://opendatacommons.org/). 

Until the release of [CC version 4](https://wiki.creativecommons.org/4.0), published in November 2013, the CC licence did not cover data. Between them, CC and ODC licences can cover all forms of digital work.

* **There are many other licence types**
* Many are bespoke
    * Bespoke licences are difficult to manage
    * Many legacy datasets have bespoke licences

![Creative Commons @love_CC_2008](https://farm4.staticflickr.com/3148/2732488224_aedf36e837_b_d.jpg)

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
    * ND – No derivatives: the licensee can not derive new content from the resource.
* Requirements
    * BY – By attribution: the licensee must attribute the source.
    * SA – Share-alike: if the licensee adapts the resource, it must be released under the same licence.
* Prohibitions
    * NC – Non commercial: the licensee must not use the work commercially without prior approval.




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


Table: [Creative Commons license combinations](https://docs.google.com/spreadsheets/d/17aT7Dj6QtE88XPS44oPQ7mVeSdY1YnZ1rlpjPvXNz0E/pub?single=true&gid=0&output=html)

\newpage

# Why are licenses important?

* They tell you what you can and can't do with 'stuff'
* Very significant when multiple datasets are combined
    * It then becomes an issue of license compatibility


![Compatibility of common open-source software licenses @Floss-license-slide-image_Wheeler_2007](https://upload.wikimedia.org/wikipedia/commons/1/1d/Floss-license-slide-image.png)

\newpage

## Which is important when we mash up data

Certain licences when combined:
    
* Are incompatible
    * Creating data islands
* Inhibit commercial exploitation (NC)
* Force the adoption of certain licences
    * If you want people to commercially exploit your stuff don't incorporate CC-BY-NC-SA data!
* Stops the derivation of *new works*



\newpage

![Islands of incompatibility [@IncompatibilitiesAndLicenceClauses_en_beck_2016]](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Incompatibilities_And_Licence_Clauses.svg/989px-Incompatibilities_And_Licence_Clauses.svg.png)

\newpage

![A conceptual licence processing workflow @ConceptualLicenceProcessingWorkflow_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/ConceptualLicenceProcessingWorkflow.svg/1024px-ConceptualLicenceProcessingWorkflow.svg.png)


A conceptual licence processing workflow. The licence processing service analyses the incoming licence metadata and determines if the data can be legally integrated and any resulting licence implications for the derived product.

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





        <iframe
            width="400"
            height="300"
            src="https://www.youtube.com/embed/jUzGF401vLc"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

## Here's something I prepared earlier

A live presentation (for those who weren't at the event).....


```python
from IPython.display import YouTubeVideo
YouTubeVideo('tkRB5Rp1_W4')

```





        <iframe
            width="400"
            height="300"
            src="https://www.youtube.com/embed/tkRB5Rp1_W4"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

# A more robust logic

* Would need to decouple licence incompatibility from licence name into licence clause (see table below)
* Deal with all licence type
* Provide recommendations based on desired derivative licence type
* Link this through to the type of process in a workflow:
    * data derivation is, from a licence position, very different to contextual display

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

Table: [Creative Commons license combinations](https://docs.google.com/spreadsheets/d/17aT7Dj6QtE88XPS44oPQ7mVeSdY1YnZ1rlpjPvXNz0E/pub?single=true&gid=0&output=html)


\newpage

# OGC and Licence interoperability

* The geo business landscape is increasingly based on integrating heterogeneous data to develop new products
* Licence heterogeneity is a barrier to data integration and interoperability
* A licence calculus can help resolve and identify heterogenties leading to
    * legal compliance
    * confidence
* Use of standards and collaboration with organisations is crucial
    * [Open Data Licensing ontology](https://github.com/theodi/open-data-licensing)
    * [The Open Data Institute](http://theodi.org/)
* Failure to do this could lead to breaches in data licenses
    * and we all know where that puts us........
    


![Breaching a data license can be serious (restricted = randomly!)](https://dl.dropboxusercontent.com/u/393477/ImageBank/Jail_Bars_Icon.png)

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

![The Semantic Web Compared To The Traditional Web @SemWeb_TradWeb_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/The_Semantic_Web_Compared_To_The_Traditional_Web.svg/1024px-The_Semantic_Web_Compared_To_The_Traditional_Web.svg.png)

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

![The Linked Open Data cloud in 2014 (@schmachtenberg_linking_2014)](http://lod-cloud.net/versions/2014-08-30/lod-cloud_colored.png)

\newpage

# Linked Data Basics

## [Four rules for Linked Data from Tim Berners Lee](https://www.w3.org/DesignIssues/LinkedData.html)

1. Use URIs as names for things
1. Use HTTP URIs so that people can look up those names.
1. When someone looks up a URI, provide useful information, using the standards (RDF*, SPARQL)
1. Include links to other URIs, so that they can discover more things.

\newpage

# The [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF) data model

RDF stores data as *triples* in the following manner:

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/12/SubjectPredicateObject-GraphRDF.svg/640px-SubjectPredicateObject-GraphRDF.svg.png)

This is a [graph model](https://en.wikipedia.org/wiki/Graph_(abstract_data_type) that consists of nodes (subject and object)) and edges (predicate).

\newpage

## Data expressed as RDF

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6b/AntAsData.svg/1024px-AntAsData.svg.png)

\newpage

## Data expressed as RDF Linked Data

![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/ba/AntAsLinkedData.svg/1024px-AntAsLinkedData.svg.png)

\newpage

## [RDF notation](https://en.wikipedia.org/wiki/Resource_Description_Framework)

RDF can be represented in different ways - each of which are interoperable. For example:

* RDF/XML, 
* Notation-3 (N3), 
* Turtle (.ttl), 
* N-Triples, 
* RDFa,
* RDF/JSON

Each represent *subject, predicate, object* triples in different ways


\newpage

## One step beyond.... Linked Open Data

### [Is your Linked Open Data 5 star](https://www.w3.org/DesignIssues/LinkedData.html)

```
★	Available on the web (whatever format) but with an open licence, to be Open Data
★★	Available as machine-readable structured data (e.g. excel instead of image scan of a table)
★★★	as (2) plus non-proprietary format (e.g. CSV instead of excel)
★★★★	All the above plus, Use open standards from W3C (RDF and SPARQL) to identify things, so that people can point at your stuff
★★★★★	All the above, plus: Link your data to other people’s data to provide context
```

![Is your data 5 star](https://www.w3.org/DesignIssues/diagrams/lod/597992118v2_350x350_Back.jpg)

\newpage

# The Supporting Semantic Web Stack

![The semantic Web Stack](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f7/Semantic_web_stack.svg/768px-Semantic_web_stack.svg.png)

\newpage

## It's about re-use

### Vocabularies

The glue that joins concepts together. 

A concept shared is a link gained. By re-using concepts it makes it easier to understand what your data means and where and how it should be re-used.



```python
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://lov.okfn.org/dataset/lov/"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

## It's about re-use

### Ontology

> An ontology is a shared formal explicit specialisation of a conceptualisation

![Technology used in Ontology definition(@SemWebOverview_en_beck_2012)](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/SemWebOverview.svg/1024px-SemWebOverview.svg.png)

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

* *conceptualisation* is identifying relevant abstracted concepts of a phenomena suited to a specific domain
* *explicit* means that the concepts are explicitly defined
* *formal* refers to the fact that the ontology should be machine-readable
* *shared* refers to notion that on ontology captures consensual knowledge

\newpage

### Ontology Example 

* A ‘Carnivore’ is a concept whose members are exactly those animals who eat only meat
* A ‘Bear’ is a concept whose members are a kind of ‘Carnivore’
* A ‘Cub’ is a concept whose members are exactly those ‘Bear’ whose age is less than one year
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

If we had other logic that told us that 'newborn' is the same as saying less than one year then we can also infer

```
'Ching Ching' is a Cub.
```

In an ontology you can say *Anything about Anything*. Whilst carnivore is a generally useful concept about *bears* it is not *specifically* useful when considering *pandas*. The domain of application is clearly important. 

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
* 'abc:isCapitalOf' (the concept for which the city is capital: stored in the variable 'y') 

The 'concept for which the city is capital' (stored in variable 'y') must also have the following concepts:

* 'abc:countryname' (the name of a country: stored in the variable 'country')
* 'abc:isInContinent' abc:Africa (isInContinent of the the individual Africa')

\newpage

## [GeoSPARQL](http://www.opengeospatial.org/projects/groups/geosparqlswg) the SQL of the spatial semantic web

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





        <iframe
            width="1000"
            height="700"
            src="http://www.opengeospatial.org/projects/groups/geosparqlswg"
            frameborder="0"
            allowfullscreen
        ></iframe>
        




```python
# Linked Data and Geo


```

\newpage

## GeoSPARQL employs spatial calculus

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/Region_Connection_Calculus_8_Relations_and_Open_Geospatial_Consortium_relations.svg/1024px-Region_Connection_Calculus_8_Relations_and_Open_Geospatial_Consortium_relations.svg.png)

\newpage

# Querying Linked Data in the wild

## The Ordnance Survey

A URI for every place in the UK



```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/doc/50kGazetteer/177276', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://data.ordnancesurvey.co.uk/doc/50kGazetteer/177276"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/id/postcodeunit/NG72QL', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://data.ordnancesurvey.co.uk/id/postcodeunit/NG72QL"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://data.ordnancesurvey.co.uk/"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/ontology/', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://data.ordnancesurvey.co.uk/ontology/"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/datasets/code-point-open/explorer/sparql', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://data.ordnancesurvey.co.uk/datasets/code-point-open/explorer/sparql"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
## Open Street Map


```


```python
from IPython.display import IFrame
IFrame('http://linkedgeodata.org/About', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://linkedgeodata.org/About"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://browser.linkedgeodata.org/', width=1000, height=700)


```





        <iframe
            width="1000"
            height="700"
            src="http://browser.linkedgeodata.org/"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

## Geonames



```python
from IPython.display import IFrame
IFrame('http://www.geonames.org/ontology/documentation.html', width=1000, height=700)


```





        <iframe
            width="1000"
            height="700"
            src="http://www.geonames.org/ontology/documentation.html"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://www.geonames.org/maps/google_52.94_358.8.html', width=1000, height=700)


```





        <iframe
            width="1000"
            height="700"
            src="http://www.geonames.org/maps/google_52.94_358.8.html"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage


```python
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/vocabs/gn', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://lov.okfn.org/dataset/lov/vocabs/gn"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

# Geo Vocabularies


```python
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/vocabs/?q=geo+space+address+geonames+os+spatial', width=1000, height=700)
```





        <iframe
            width="1000"
            height="700"
            src="http://lov.okfn.org/dataset/lov/vocabs/?q=geo+space+address+geonames+os+spatial"
            frameborder="0"
            allowfullscreen
        ></iframe>
        



\newpage

# Conclusions

* Technical interoperability is only one part of the problem
* Open data will become increasingly important as governments and other groups release resources under clear licences
    * Licences are a barrier to re-use
* Data shows its true value when combined with other data sources – linked data creates an opportunity
* Usability: common data model and reference of common URIs (for example, postcodes) allows for easy data aggregation and integration.
* Shift in focus from cartography and geometries to ‘things’ and the relationships between them.
* Spatial no longer special – part of the bigger information world....
* location is a very important information hub and provides a key underpinning reference framework which brings many datasets together and provides important context.

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

If X is spatiallyWithin Y and Y is spatiallyWithin Z then X is spatiallyWithin Z.

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

![Processing transparency between open and closed systems](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Processing_transparency_between_open_and_closed_systems.svg/630px-Processing_transparency_between_open_and_closed_systems.svg.png)

\newpage

# References
