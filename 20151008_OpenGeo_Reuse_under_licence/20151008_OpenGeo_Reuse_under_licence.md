
![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/20151008_Re-UseUnderLicence.png)


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
commandLineSyntax = 'ipython nbconvert --to markdown 20151008_OpenGeo_Reuse_under_licence.ipynb'
print (commandLineSyntax)

os.system(commandLineSyntax)

### Export this notebook and the document header as PDF using Pandoc

commandLineSyntax = 'pandoc  -f markdown -t latex -N -V geometry:margin=1in DocumentHeader.md 20151008_OpenGeo_Reuse_under_licence.md --filter pandoc-citeproc  --latex-engine=xelatex --toc -o interim.pdf '

os.system(commandLineSyntax)

### Remove cruft from the pdf

commandLineSyntax = 'pdftk interim.pdf cat 1-3 16-end output 20151008_OpenGeo_Reuse_under_licence.pdf'

os.system(commandLineSyntax)

### Remove the interim pdf

commandLineSyntax = 'rm interim.pdf'

os.system(commandLineSyntax)

### Export this notebook as markdown
commandLineSyntax = 'ipython nbconvert --to markdown 20151008_OpenGeo_Reuse_under_licence.ipynb'
print (commandLineSyntax)

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

    Installed watermark.py. To use it, type:
      %load_ext watermark



```python
%watermark -a "Anthony Beck"  -d -v -m -g
```

    Anthony Beck 29/06/2015 
    
    CPython 2.7.10
    IPython 3.2.0
    
    compiler   : GCC 4.4.7 20120313 (Red Hat 4.4.7-1)
    system     : Linux
    release    : 3.13.0-37-generic
    machine    : x86_64
    processor  : x86_64
    CPU cores  : 4
    interpreter: 64bit
    Git hash   : 



```python
#List of installed conda packages
!conda list
```

    # packages in environment at /home/arb/LocalPython/Anaconda27/anaconda:
    #
    _license                  1.1                      py27_0  
    abstract-rendering        0.5.1                np19py27_0  
    accelerate                1.11.0              np19py27_p0  
    affine                    1.1.0                    py27_0  
    alabaster                 0.7.3                    py27_0  
    anaconda                  2.2.0                np19py27_0  
    argcomplete               0.8.4                    py27_0  
    arrow                     0.5.4                     <pip>
    astroid                   1.3.6                     <pip>
    astropy                   1.0.2                np19py27_0  
    babel                     1.3                      py27_0  
    backports.ssl-match-hostname 3.4.0.2                   <pip>
    basemap                   1.0.7                np19py27_0  
    bcolz                     0.8.1                np19py27_0  
    beautiful-soup            4.3.2                    py27_0  
    beautifulsoup4            4.3.2                     <pip>
    binstar                   0.10.3                   py27_0  
    bitarray                  0.8.1                    py27_0  
    blaze                     0.8.0                     <pip>
    blaze-core                0.8.0                np19py27_0  
    blz                       0.6.2                np19py27_0  
    bokeh                     0.8.2                np19py27_0  
    boto                      2.38.0                   py27_0  
    bottle                    0.12.7                   py27_0  
    brewer2mpl                1.4                      py27_0  
    cairo                     1.12.18                       4  
    cartopy                   0.10.0               np18py27_0  
    cdecimal                  2.3                      py27_0  
    certifi                   14.05.14                 py27_0  
    cffi                      0.9.2                    py27_0  
    click                     4.0                      py27_0  
    cligj                     0.1.0                    py27_0  
    cloog                     0.18.0                        0  
    clyent                    0.3.4                    py27_0  
    colorama                  0.3.3                    py27_0  
    conda                     3.14.0                   py27_0  
    conda-build               1.12.1                   py27_0  
    conda-env                 2.2.3                    py27_0  
    configobj                 5.0.6                    py27_0  
    cryptography              0.8.2                    py27_0  
    cudatoolkit               6.0                          p0  
    curl                      7.38.0                        0  
    cython                    0.22                     py27_0  
    cytoolz                   0.7.2                    py27_0  
    datashape                 0.4.5                np19py27_0  
    dateutil                  2.4.1                    py27_0  
    decorator                 3.4.0                    py27_0  
    descartes                 1.0.1                    py27_0  
    docutils                  0.12                     py27_0  
    dynd-python               0.6.5                np19py27_0  
    enum                      0.4.4                     <pip>
    enum34                    1.0.4                    py27_0  
    fastcache                 1.0.2                    py27_0  
    fiona                     1.5.1                np19py27_0  
    flask                     0.10.1                   py27_1  
    fontconfig                2.11.1                        4  
    freetype                  2.5.2                         2  
    funcsigs                  0.4                      py27_0  
    futures                   2.2.0                    py27_0  
    gdal                      1.11.2               np19py27_2  
    geopandas                 0.1.1                    py27_0  
    geopy                     1.10.0                    <pip>
    geos                      3.3.3                         0  
    gevent                    1.0.1                    py27_0  
    gevent-websocket          0.9.3                    py27_0  
    glib                      2.43.0                        2  
    gmp                       5.1.2                         2  
    greenlet                  0.4.6                    py27_0  
    grin                      1.2.1                    py27_1  
    h5py                      2.5.0                np19py27_0  
    harfbuzz                  0.9.35                        6  
    hdf5                      1.8.14                        0  
    html5lib                  0.99999                   <pip>
    ipython                   3.2.0                    py27_0  
    ipython-notebook          3.2.0                    py27_0  
    ipython-qtconsole         3.1.0                    py27_0  
    isl                       0.12.2                        0  
    itsdangerous              0.24                     py27_0  
    jdcal                     1.0                      py27_0  
    jedi                      0.8.1                    py27_0  
    jinja2                    2.7.3                    py27_1  
    jpeg                      8d                            0  
    jsonschema                2.4.0                    py27_0  
    libdynd                   0.6.5                         0  
    libffi                    3.0.13                        0  
    libgcc                    4.8.4                         1  
    libgdal                   1.11.2                        0  
    libnetcdf                 4.3.2                         1  
    libpng                    1.6.17                        0  
    libsodium                 0.4.5                         0  
    libtiff                   4.0.2                         1  
    libxml2                   2.9.0                         0  
    libxslt                   1.1.28                        0  
    llvmlite                  0.4.0                    py27_0  
    logilab-common            0.63.2                    <pip>
    lxml                      3.4.4                    py27_0  
    mapnik                    0.1                       <pip>
    markupsafe                0.23                     py27_0  
    matplotlib                1.4.3                np19py27_2  
    mistune                   0.6                      py27_0  
    mkl                       11.1                np19py27_p3  
    mkl-rt                    11.1                         p0  
    mkl-service               1.0.0                   py27_p1  
    mklfft                    2.0                 np19py27_p0  
    mock                      1.0.1                    py27_0  
    mpc                       1.0.1                         0  
    mpfr                      3.1.2                         0  
    multipledispatch          0.4.7                    py27_0  
    ncurses                   5.9                           4  
    networkx                  1.9.1                    py27_0  
    nltk                      3.0.2                np19py27_0  
    nose                      1.3.6                    py27_0  
    notedown                  1.4.4                     <pip>
    numba                     0.18.2               np19py27_1  
    numbapro                  0.18.0              np19py27_p2  
    numbapro_cudalib          0.2                           0  
    numexpr                   2.3.1               np19py27_p0  [mkl]
    numpy                     1.9.2                   py27_p0  [mkl]
    odo                       0.3.2                np19py27_0  
    openpyxl                  2.0.2                    py27_0  
    openssl                   1.0.1k                        1  
    pandana                   0.1.2                    py27_0  
    pandas                    0.16.2               np19py27_0  
    pandasql                  0.6.2                np19py27_0  
    pandoc-attributes         0.1.7                     <pip>
    pandocfilters             1.2.4                     <pip>
    pango                     1.36.8                        3  
    patchelf                  0.6                           0  
    patsy                     0.3.0                np19py27_0  
    pcre                      8.31                          0  
    pep8                      1.6.2                    py27_0  
    pillow                    2.7.0                    py27_1  
    pip                       7.0.3                    py27_0  
    pixman                    0.26.2                        0  
    plotly                    1.6.17                    <pip>
    ply                       3.6                      py27_0  
    prettyplotlib             0.1.7                     <pip>
    prettytable               0.7.2                    py27_0  
    proj4                     4.8.0                         0  
    psutil                    2.2.1                    py27_0  
    ptyprocess                0.4                      py27_0  
    py                        1.4.26                   py27_0  
    py2cairo                  1.10.0                   py27_2  
    pyasn1                    0.1.7                    py27_0  
    pycosat                   0.6.1                    py27_0  
    pycparser                 2.12                     py27_0  
    pycrypto                  2.6.1                    py27_0  
    pycurl                    7.19.5.1                 py27_0  
    pyflakes                  0.8.1                    py27_0  
    pygments                  2.0.2                    py27_0  
    pylint                    1.4.3                     <pip>
    pymc                      2.3.4               np19py27_p0  [mkl]
    pyopenssl                 0.15.1                   py27_0  
    pyparsing                 2.0.3                    py27_0  
    pyproj                    1.9.3                    py27_0  
    pyqt                      4.11.3                   py27_1  
    pysal                     1.6.0                np19py27_1  
    pyshp                     1.2.1                     <pip>
    pytables                  3.1.1                np19py27_2  
    pytest                    2.7.0                    py27_0  
    python                    2.7.10                        0  
    python-dateutil           2.4.2                    py27_0  
    pytz                      2015.4                   py27_0  
    pyyaml                    3.11                     py27_1  
    pyzmq                     14.7.0                   py27_0  
    qt                        4.8.6                         3  
    r                         3.1.3                         0  
    r-base                    3.1.3                         2  
    r-boot                    1.3_16                 r3.1.3_0  
    r-class                   7.3_12                 r3.1.3_0  
    r-cluster                 1.15.3                        0  
    r-codetools               0.2_11                 r3.1.3_0  
    r-foreign                 0.8_63                 r3.1.3_0  
    r-kernsmooth              2.23_14                r3.1.3_0  
    r-lattice                 0.20_31                r3.1.3_0  
    r-mass                    7.3.37                        0  
    r-matrix                  1.2_1                  r3.1.3_0  
    r-mgcv                    1.8_6                  r3.1.3_0  
    r-nlme                    3.1.118                       0  
    r-nlme                    3.1_120                r3.1.3_0  
    r-nnet                    7.3_9                  r3.1.3_0  
    r-recommended             3.1.3                         0  
    r-rpart                   4.1_9                  r3.1.3_0  
    r-spatial                 7.3_9                  r3.1.3_0  
    r-survival                2.38_2                 r3.1.3_0  
    rasterio                  0.15.1                   py27_0  
    readline                  6.2                           2  
    redis                     2.6.9                         0  
    redis-py                  2.10.3                   py27_0  
    requests                  2.7.0                    py27_0  
    rope                      0.9.4                    py27_1  
    rpy2                      2.5.6                    py27_0  
    runipy                    0.1.3                    py27_0  
    scikit-image              0.11.3               np19py27_0  
    scikit-learn              0.16.1              np19py27_p0  [mkl]
    scipy                     0.15.1              np19py27_p0  [mkl]
    seaborn                   0.5.1                     <pip>
    setuptools                17.1.1                   py27_0  
    shapely                   1.5.9                     <pip>
    simplejson                3.6.3                    py27_0  
    singledispatch            3.4.0.3                  py27_1  
    sip                       4.16.5                   py27_0  
    six                       1.9.0                    py27_0  
    snowballstemmer           1.2.0                    py27_0  
    snuggs                    1.3.1                     <pip>
    sockjs-tornado            1.0.1                    py27_0  
    sphinx                    1.3.1                    py27_0  
    sphinx-rtd-theme          0.1.7                     <pip>
    sphinx_rtd_theme          0.1.7                    py27_0  
    spyder                    2.3.4                    py27_1  
    spyder-app                2.3.4                    py27_0  
    sqlalchemy                1.0.3                    py27_0  
    sqlite                    3.8.4.1                       1  
    sqlparse                  0.1.14                   py27_0  
    ssl_match_hostname        3.4.0.2                  py27_0  
    statsmodels               0.6.1                np19py27_0  
    sympy                     0.7.6                    py27_0  
    system                    5.8                           2  
    tables                    3.1.1                     <pip>
    terminado                 0.5                      py27_0  
    theano                    0.7.0                np19py27_0  
    tk                        8.5.18                        0  
    toolz                     0.7.2                    py27_0  
    tornado                   4.2                      py27_0  
    tweepy                    2.3                      py27_0  
    twitter                   1.17.0                    <pip>
    ujson                     1.33                     py27_0  
    unicodecsv                0.9.4                    py27_0  
    urbansim                  2.0.1                     <pip>
    util-linux                2.21                          0  
    werkzeug                  0.10.4                   py27_0  
    xlrd                      0.9.3                    py27_0  
    xlsxwriter                0.7.2                    py27_0  
    xlwt                      1.0.0                    py27_0  
    yaml                      0.1.6                         0  
    zeromq                    4.0.5                         0  
    zlib                      1.2.8                         0  



```python
#List of installed pip packages
!pip list
```

    abstract-rendering (0.5.1)
    affine (1.1.0)
    alabaster (0.7.3)
    argcomplete (0.8.4)
    arrow (0.5.4)
    astroid (1.3.6)
    astropy (1.0.2)
    Babel (1.3)
    backports.ssl-match-hostname (3.4.0.2)
    basemap (1.0.7)
    bcolz (0.8.1)
    beautifulsoup4 (4.3.2)
    binstar (0.10.3)
    bitarray (0.8.1)
    blaze (0.8.0)
    blz (0.6.2)
    bokeh (0.8.2)
    boto (2.38.0)
    bottle (0.12.7)
    brewer2mpl (1.4.1)
    Cartopy (0.10.0)
    cdecimal (2.3)
    certifi (14.5.14)
    cffi (0.9.2)
    click (4.0)
    cligj (0.1.0)
    clyent (0.3.4)
    colorama (0.3.3)
    conda (3.14.0)
    conda-build (1.12.1)
    conda-env (2.2.3)
    configobj (5.0.6)
    cryptography (0.8.2)
    Cython (0.22)
    cytoolz (0.7.2)
    datashape (0.4.5)
    decorator (3.4.0)
    descartes (1.0.1)
    docutils (0.12)
    enum (0.4.4)
    enum34 (1.0.4)
    fastcache (1.0.2)
    Fiona (1.5.1)
    Flask (0.10.1)
    funcsigs (0.4)
    futures (2.2.0)
    GDAL (1.11.2)
    geopandas (0.1.1)
    geopy (1.10.0)
    gevent (1.0.1)
    gevent-websocket (0.9.3)
    greenlet (0.4.6)
    grin (1.2.1)
    h5py (2.5.0)
    html5lib (0.99999)
    ipython (3.2.0)
    itsdangerous (0.24)
    jdcal (1.0)
    jedi (0.8.1)
    Jinja2 (2.7.3)
    jsonschema (2.4.0)
    llvmlite (0.4.0)
    logilab-common (0.63.2)
    lxml (3.4.4)
    mapnik (0.1)
    MarkupSafe (0.23)
    matplotlib (1.4.3)
    mistune (0.6)
    mklfft (0.0.0)
    mock (1.0.1)
    multipledispatch (0.4.7)
    networkx (1.9.1)
    nltk (3.0.2)
    nose (1.3.6)
    notedown (1.4.4)
    numba (0.18.2)
    numbapro (0.18.0)
    numexpr (2.3.1)
    numpy (1.9.2)
    odo (0.3.2)
    openpyxl (2.0.2)
    pandana (0.1.2)
    pandas (0.16.2)
    pandasql (0.6.2)
    pandoc-attributes (0.1.7)
    pandocfilters (1.2.4)
    patsy (0.3.0)
    pep8 (1.6.2)
    Pillow (2.7.0)
    pip (7.0.3)
    plotly (1.6.17)
    ply (3.6)
    prettyplotlib (0.1.7)
    prettytable (0.7.2)
    psutil (2.2.1)
    ptyprocess (0.4)
    py (1.4.26)
    pyasn1 (0.1.7)
    pycosat (0.6.1)
    pycparser (2.12)
    pycrypto (2.6.1)
    pycurl (7.19.5.1)
    pyflakes (0.8.1)
    Pygments (2.0.2)
    pylint (1.4.3)
    pymc (2.3.4)
    pyOpenSSL (0.15.1)
    pyparsing (2.0.3)
    pyproj (1.9.4)
    PySAL (1.6.0)
    pyshp (1.2.1)
    pytest (2.7.0)
    python-dateutil (2.4.2)
    pytz (2015.4)
    PyYAML (3.11)
    pyzmq (14.7.0)
    rasterio (0.23.0)
    redis (2.10.3)
    requests (2.7.0)
    rope (0.9.4)
    rpy2 (2.5.6)
    runipy (0.1.3)
    scikit-image (0.11.3)
    scikit-learn (0.16.1)
    scipy (0.15.1)
    seaborn (0.5.1)
    setuptools (17.1.1)
    Shapely (1.5.9)
    simplejson (3.6.3)
    singledispatch (3.4.0.3)
    six (1.9.0)
    snowballstemmer (1.2.0)
    snuggs (1.3.1)
    sockjs-tornado (1.0.1)
    Sphinx (1.2.3)
    sphinx-rtd-theme (0.1.7)
    spyder (2.3.4)
    SQLAlchemy (1.0.3)
    sqlparse (0.1.14)
    statsmodels (0.6.1)
    sympy (0.7.6)
    tables (3.1.1)
    terminado (0.5)
    Theano (0.7.0)
    toolz (0.7.2)
    tornado (4.2)
    tweepy (2.3.0)
    twitter (1.17.0)
    ujson (1.33)
    unicodecsv (0.9.4)
    urbansim (2.0.1)
    Werkzeug (0.10.4)
    xlrd (0.9.3)
    XlsxWriter (0.7.2)
    xlwt (1.0.0)


## Running dynamic presentations

You need to install the [RISE Ipython Library](https://github.com/damianavila/RISE) from [Damián Avila](https://github.com/damianavila) for dynamic presentations

To convert and run this as a static presentation run the following command:


```python
!ipython nbconvert 20151008_OpenGeo_Reuse_under_licence.ipynb --to slides --post serve
```

    /home/arb/LocalPython/Anaconda27/anaconda/lib/python2.7/site-packages/IPython/nbconvert.py:13: ShimWarning: The `IPython.nbconvert` package has been deprecated. You should import from ipython_nbconvert instead.
      "You should import from ipython_nbconvert instead.", ShimWarning)
    [NbConvertApp] Converting notebook 20151008_OpenGeo_Reuse_under_licence.ipynb to slides
    [NbConvertApp] Writing 257738 bytes to 20151008_OpenGeo_Reuse_under_licence.slides.html
    [NbConvertApp] Redirecting reveal.js requests to https://cdn.jsdelivr.net/reveal.js/2.6.2
    Serving your slides at http://127.0.0.1:8000/20151008_OpenGeo_Reuse_under_licence.slides.html
    Use Control-C to stop this server
    Created new window in existing browser session.
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 2.68ms
    WARNING:tornado.access:404 GET /favicon.ico (127.0.0.1) 0.96ms


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

* Research Fellow, University of Nottingham: [orcid](http://orcid.org/0000-0002-2991-811X)
* Director, Geolytics Limited - A spatial data analytics consultancy

## About this presentation

* [Available on GitHub](https://github.com/AntArch/Presentations_Github/tree/master/20151008_OpenGeo_Reuse_under_licence) - https://github.com/AntArch/Presentations_Github/
* [Fully referenced PDF](https://github.com/AntArch/Presentations_Github/blob/master/20150916_OGC_Reuse_under_licence/20151008_OpenGeo_Reuse_under_licence.pdf)


\newpage

# A potted history of mapping

## In the beginning was the geoword

and the word was ***cartography***

![The lens of cartography @TheLensOfCartography_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/TheLensOfCartography.svg/1024px-TheLensOfCartography.svg.png)


\newpage

![A static map (public domain)](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/Claudius_Ptolemy-_The_World.jpg/1024px-Claudius_Ptolemy-_The_World.jpg)

Cartography was king. Static representations of spatial knowledge with the cartographer deciding what to represent.

\newpage

# And then there was data .........




![Data @Data_types_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Data_types_-_en.svg/738px-Data_types_-_en.svg.png)

\newpage

![But the data was siloed (restricted use)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/TheEndOfThe20thCentury.png)

Restrictive data

\newpage

![Concerted efforts to de-silo data and make data interoperable (restricted use)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/TheCatalyst.png)

Making data interoperable and open

\newpage

# Technical interoperability - levelling the field

![Interoperable integration of spatial data - the technological issues @TechnicalInteroperableIntegrationOfSpatialData_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/TechnicalInteroperableIntegrationOfSpatialData.svg/1024px-TechnicalInteroperableIntegrationOfSpatialData.svg.png)

\newpage

## Facilitating data driven visualization

![From Map to Model The changing paradigm of map creation from cartography to data driven visualization @FromMapToModel_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/FromMapToModel.svg/1024px-FromMapToModel.svg.png)

From Map to Model The changing paradigm of map creation from cartography to data driven visualization

\newpage

![Local To Global integration of data to create multiple generic products @Local_To_Global_integration_of_data_to_create_multiple_generic_products_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Local_To_Global_integration_of_data_to_create_multiple_generic_products.svg/1024px-Local_To_Global_integration_of_data_to_create_multiple_generic_products.svg.png)

\newpage

![A new working paradigm (public domain)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/ANewWorkingParadigm.png)

\newpage

![Cartography is no longer key. Spatial mapping is now about the the formal and informal data stack. Elements such as provenance, credibility are much more important for use and re-use of this data. @CartographyNoLongerKing_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/CartographyNoLongerKing.svg/1024px-CartographyNoLongerKing.svg.png)

\newpage

# What about non-technical interoperability issues?


![The full stack that enables interoperable integration of spatial data @InteroperableIntegrationOfSpatialData_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/InteroperableIntegrationOfSpatialData.svg/500px-InteroperableIntegrationOfSpatialData.svg.png)

Issues surrounding non-technical interoperability include:
    
* Policy interoperabilty
* Licence interoperability
* Legal interoperability
* Social interoperability

We will focus on licence interoperability
    

\newpage

![The modern data landscape (restricted)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/20151008_Re-UseUnderLicence.png)

There is a multitude of formal and informal data. 

\newpage

![Some licences @rdflicense_2015](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/SomeLicences_FromRDFLicences.png)

Each of these data objects can be licenced in a different way. This shows some of the licences described by the RDFLicence ontology

\newpage

## What is a licence?

[Wikipedia state:](https://en.wikipedia.org/wiki/License)

> A license may be granted by a party ("licensor") to another party ("licensee") as an element of an agreement between those parties. 

> A shorthand definition of a license is "an authorization (by the licensor) to use the licensed material (by the licensee)."



![A licence describes what you can and cannot do to a data object @licence_classification_2015](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForOGC/Licence_Constraints.png)

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

License|Reproduction|Distribution|Derivation|ND|BY|SA|NC
----|----|----|----|----|----|----|----
CC0|X|X|X||||
CC-BY-ND|X|X||X|X||
CC-BY-NC-ND|X|X||X|X||X
CC-BY|X|X|X||X||
CC-BY-SA|X|X|X||X|X|
CC-BY-NC|X|X|X||X||X
CC-BY-NC-SA|X|X|X||X|X|X

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
* etc..... for discussion?

License|Reproduction|Distribution|Derivation|ND|BY|SA|NC
----|----|----|----|----|----|----|----
CC0|X|X|X||||
CC-BY-ND|X|X||X|X||
CC-BY-NC-ND|X|X||X|X||X
CC-BY|X|X|X||X||
CC-BY-SA|X|X|X||X|X|
CC-BY-NC|X|X|X||X||X
CC-BY-NC-SA|X|X|X||X|X|X

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

# Questions

In terms of discussion I'm interested in how these issues affect you.........

![Processing transparency between open and closed systems](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Processing_transparency_between_open_and_closed_systems.svg/630px-Processing_transparency_between_open_and_closed_systems.svg.png)

\newpage

# References
