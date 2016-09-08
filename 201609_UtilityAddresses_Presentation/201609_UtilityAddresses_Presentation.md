
# Maximising the utility of an Open Address

Anthony Beck (GeoLytics), John Daniels (UU), Paul Williams (UU), Dave Pearson (UU), Matt Beare (Beare Essentials)


![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/UU_SPA_CONCEPTUAL.png)


Go down for licence and other metadata about this presentation

\newpage

# The view of addressing from United Utilities

Unless states otherwise all content is under a CC-BY licence. All images are re-used under licence - follow the image URL for the licence conditions.

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/CC_BY.png)


You can access this presentation on github:

[https://github.com/AntArch/20150305_AddressDay.git](https://github.com/AntArch/20150305_AddressDay.git)


![](https://dl.dropboxusercontent.com/u/393477/ImageBank/Lego_Head_ARB.png)


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
commandLineSyntax = 'ipython nbconvert --to markdown 201609_UtilityAddresses_Presentation.ipynb'
print (commandLineSyntax)

os.system(commandLineSyntax)

### Export this notebook and the document header as PDF using Pandoc

commandLineSyntax = 'pandoc  -f markdown -t latex -N -V geometry:margin=1in DocumentHeader.md 201609_UtilityAddresses_Presentation.md --filter pandoc-citeproc  --latex-engine=xelatex --toc -o interim.pdf '

os.system(commandLineSyntax)

### Remove cruft from the pdf

commandLineSyntax = 'pdftk interim.pdf cat 1-5 22-end output 201609_UtilityAddresses_Presentation.pdf'

os.system(commandLineSyntax)

### Remove the interim pdf

commandLineSyntax = 'rm interim.pdf'

os.system(commandLineSyntax)
```

    ipython nbconvert --to markdown 201609_UtilityAddresses_Presentation.ipynb





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


```python
%watermark -a "Anthony Beck"  -d -v -m -g
```

    Anthony Beck 2016-08-30 
    
    CPython 3.5.2
    IPython 5.0.0
    
    compiler   : GCC 4.4.7 20120313 (Red Hat 4.4.7-1)
    system     : Linux
    release    : 4.4.0-31-generic
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
    Using Anaconda API: https://api.anaconda.org
    _license                  1.1                      py27_0    <unknown>
    abstract-rendering        0.5.1                np19py27_0    <unknown>
    beautiful-soup            4.3.2                    py27_0    <unknown>
    bitarray                  0.8.1                    py27_0    <unknown>
    cdecimal                  2.3                      py27_0    <unknown>
    certifi                   14.05.14                 py27_0    <unknown>
    clyent                    0.3.4                    py27_0    <unknown>
    colorama                  0.3.3                    py27_0    <unknown>
    configobj                 5.0.6                    py27_0    <unknown>
    docutils                  0.12                     py27_0    <unknown>
    dynd-python               0.6.5                np19py27_0    <unknown>
    enum34                    1.0.4                    py27_0    <unknown>
    fastcache                 1.0.2                    py27_0    <unknown>
    flask                     0.10.1                   py27_1    <unknown>
    funcsigs                  0.4                      py27_0    <unknown>
    gevent                    1.0.1                    py27_0    <unknown>
    gevent-websocket          0.9.3                    py27_0    <unknown>
    grin                      1.2.1                    py27_1    <unknown>
    itsdangerous              0.24                     py27_0    <unknown>
    jdcal                     1.0                      py27_0    <unknown>
    jedi                      0.8.1                    py27_0    <unknown>
    jpeg                      8d                            0    <unknown>
    jsonschema                2.4.0                    py27_0    <unknown>
    libdynd                   0.6.5                         0    <unknown>
    libffi                    3.0.13                        0    <unknown>
    libtiff                   4.0.2                         1    <unknown>
    libxslt                   1.1.28                        0    <unknown>
    markupsafe                0.23                     py27_0    <unknown>
    mock                      1.0.1                    py27_0    <unknown>
    multipledispatch          0.4.7                    py27_0    <unknown>
    patsy                     0.3.0                np19py27_0    <unknown>
    pep8                      1.6.2                    py27_0    <unknown>
    pixman                    0.26.2                        0    <unknown>
    psutil                    2.2.1                    py27_0    <unknown>
    ptyprocess                0.4                      py27_0    <unknown>
    py2cairo                  1.10.0                   py27_2    <unknown>
    pyasn1                    0.1.7                    py27_0    <unknown>
    pycosat                   0.6.1                    py27_0    <unknown>
    pycrypto                  2.6.1                    py27_0    <unknown>
    pygments                  2.0.2                    py27_0    <unknown>
    redis                     2.6.9                         0    <unknown>
    redis-py                  2.10.3                   py27_0    <unknown>
    rope                      0.9.4                    py27_1    <unknown>
    runipy                    0.1.3                    py27_0    <unknown>
    ssl_match_hostname        3.4.0.2                  py27_0    <unknown>
    statsmodels               0.6.1                np19py27_0    <unknown>
    ujson                     1.33                     py27_0    <unknown>
    unicodecsv                0.9.4                    py27_0    <unknown>
    util-linux                2.21                          0    <unknown>
    _nb_ext_conf              0.3.0                    py27_0  
    accelerate                1.11.0              np19py27_p0  
    affine                    1.2.0                     <pip>
    alabaster                 0.7.3                    py27_0  
    alabaster                 0.7.6                     <pip>
    anaconda                  2.3.0                np19py27_0  
    anaconda-client           1.5.1                    py27_0  
    aniso8601                 1.1.0                     <pip>
    argcomplete               0.8.9                    py27_0  
    argcomplete               0.9.0                     <pip>
    arrow                     0.5.4                     <pip>
    astroid                   1.3.6                     <pip>
    astropy                   1.0.3                     <pip>
    astropy                   1.0.3                np19py27_0  
    babel                     1.3                      py27_0  
    backports                 1.0                      py27_0  
    backports_abc             0.4                      py27_0  
    bcolz                     0.9.0                     <pip>
    bcolz                     0.9.0                np19py27_0  
    beautifulsoup4            4.4.0                     <pip>
    binstar                   0.11.0                   py27_0  
    blaze-core                0.8.0                np19py27_0  
    blz                       0.6.2                np19py27_1  
    bokeh                     0.9.0                np19py27_0  
    bokeh                     0.9.1                     <pip>
    boto                      2.38.0                   py27_0  
    bottle                    0.12.8                    <pip>
    bottleneck                1.0.0                np19py27_0  
    bqplot                    0.3.8                     <pip>
    brewer2mpl                1.4.1                     <pip>
    cairo                     1.12.18                       4  
    Cartopy                   0.13.0                    <pip>
    certifi                   2015.04.28                <pip>
    cffi                      1.1.0                    py27_0  
    cffi                      1.1.2                     <pip>
    click                     4.0                       <pip>
    click                     4.0                      py27_0  
    cligj                     0.1.0                    py27_0  
    cligj                     0.2.0                     <pip>
    conda                     4.1.11                   py27_0  
    conda-build               1.12.1                   py27_0  
    conda-env                 2.5.2                    py27_0  
    coverage                  4.0.1                     <pip>
    cryptography              0.9.1                    py27_0  
    cudatoolkit               6.0                          p0  
    curl                      7.43.0                        0  
    Cython                    0.22.1                    <pip>
    cython                    0.22.1                   py27_0  
    cytoolz                   0.7.3                     <pip>
    cytoolz                   0.7.3                    py27_0  
    rise                      4.0.0b1                  py27_0    damianavila82
    datashape                 0.4.5                np19py27_0  
    decorator                 3.4.2                    py27_0  
    descartes                 1.0.1                     <pip>
    docopt                    0.6.2                    py27_0  
    enum                      0.4.4                     <pip>
    fiona                     1.5.1                np19py27_0  
    Flask-RESTful             0.3.4                     <pip>
    folium                    0.1.6                     <pip>
    fontconfig                2.11.1                        4  
    freetype                  2.5.2                         2  
    functools32               3.2.3.post1               <pip>
    futures                   3.0.3                     <pip>
    futures                   3.0.3                    py27_0  
    gdal                      2.0.0                    py27_1  
    geopy                     1.10.0                    <pip>
    geos                      3.3.3                         0  
    get_terminal_size         1.0.0                    py27_0  
    gevent                    1.0.2                     <pip>
    gevent-websocket          0.9.5                     <pip>
    greenlet                  0.4.7                     <pip>
    greenlet                  0.4.7                    py27_0  
    h5py                      2.5.0                np19py27_3  
    hdf5                      1.8.15.1                      1  
    html5lib                  0.999                    py27_0  
    html5lib                  0.99999                   <pip>
    tweepy                    2.3                      py27_0    https://conda.binstar.org/activisiongamescience
    basemap                   1.0.7                np19py27_0    https://conda.binstar.org/anaconda
    dateutil                  2.4.1                    py27_0    https://conda.binstar.org/anaconda
    r-matrix                  1.2_1                  r3.1.3_0    https://conda.binstar.org/asmeurer
    r-nlme                    3.1.118                       0    https://conda.binstar.org/asmeurer
    pystretch                 0.2.1                    py27_0    https://conda.binstar.org/auto
    isodate                   0.5.1                    py27_1    https://conda.binstar.org/ioos
    rdflib                    4.2.0                    py27_1    https://conda.binstar.org/ioos
    sparqlwrapper             1.6.4                    py27_1    https://conda.binstar.org/ioos
    affine                    1.1.0                    py27_0    https://conda.binstar.org/jesserobertson
    rasterio                  0.15.1                   py27_0    https://conda.binstar.org/jesserobertson
    proj4                     4.8.0                         0    https://conda.binstar.org/osgeo
    cloog                     0.18.0                        0    https://conda.binstar.org/r
    glib                      2.43.0                        2    https://conda.binstar.org/r
    gmp                       5.1.2                         2    https://conda.binstar.org/r
    harfbuzz                  0.9.35                        6    https://conda.binstar.org/r
    isl                       0.12.2                        0    https://conda.binstar.org/r
    libgcc                    4.8.4                         1    https://conda.binstar.org/r
    mpc                       1.0.1                         0    https://conda.binstar.org/r
    mpfr                      3.1.2                         0    https://conda.binstar.org/r
    ncurses                   5.9                           4    https://conda.binstar.org/r
    pango                     1.36.8                        3    https://conda.binstar.org/r
    r                         3.1.3                         0    https://conda.binstar.org/r
    r-base                    3.1.3                         2    https://conda.binstar.org/r
    r-boot                    1.3_16                 r3.1.3_0    https://conda.binstar.org/r
    r-class                   7.3_12                 r3.1.3_0    https://conda.binstar.org/r
    r-cluster                 1.15.3                        0    https://conda.binstar.org/r
    r-codetools               0.2_11                 r3.1.3_0    https://conda.binstar.org/r
    r-foreign                 0.8_63                 r3.1.3_0    https://conda.binstar.org/r
    r-kernsmooth              2.23_14                r3.1.3_0    https://conda.binstar.org/r
    r-mass                    7.3.37                        0    https://conda.binstar.org/r
    r-mgcv                    1.8_6                  r3.1.3_0    https://conda.binstar.org/r
    r-nnet                    7.3_9                  r3.1.3_0    https://conda.binstar.org/r
    r-recommended             3.1.3                         0    https://conda.binstar.org/r
    r-rpart                   4.1_9                  r3.1.3_0    https://conda.binstar.org/r
    r-spatial                 7.3_9                  r3.1.3_0    https://conda.binstar.org/r
    r-survival                2.38_2                 r3.1.3_0    https://conda.binstar.org/r
    rpy2                      2.5.6                    py27_0    https://conda.binstar.org/r
    pysptools                 0.13.0                   py27_0    https://conda.binstar.org/rbacher
    spectral                  0.16.1               np19py27_0    https://conda.binstar.org/rbacher
    cartopy                   0.10.0               np18py27_0    https://conda.binstar.org/scitools
    descartes                 1.0.1                    py27_0    https://conda.binstar.org/sel
    geopandas                 0.1.1                    py27_0    https://conda.binstar.org/sel
    pyproj                    1.9.3                    py27_0    https://conda.binstar.org/sel
    tabulate                  0.7.5                    py27_0    https://conda.binstar.org/steven_c
    bottle                    0.12.7                   py27_0    https://conda.binstar.org/synthicity
    brewer2mpl                1.4                      py27_0    https://conda.binstar.org/synthicity
    pandana                   0.1.2                    py27_0    https://conda.binstar.org/synthicity
    prettytable               0.7.2                    py27_0    https://conda.binstar.org/synthicity
    simplejson                3.6.3                    py27_0    https://conda.binstar.org/synthicity
    igraph                    0.7.1                         1    https://conda.binstar.org/yasserglez
    hypothesis                3.1.1                     <pip>
    idna                      2.0                       <pip>
    idna                      2.0                      py27_0  
    igraph                    0.1.8                     <pip>
    ipaddress                 1.0.7                    py27_0  
    ipykernel                 4.4.1                    py27_0  
    ipyparallel               5.0.1                    py27_0  
    ipython                   4.2.0                    py27_0  
    IPython-Dashboard         0.1.5                     <pip>
    ipython-notebook          3.2.0                    py27_0  
    ipython-qtconsole         3.2.0                    py27_0  
    ipython_genutils          0.1.0                    py27_0  
    ipywidgets                4.0.2                    py27_0  
    jedi                      0.9.0                     <pip>
    jinja2                    2.7.3                    py27_1  
    jsonschema                2.5.1                     <pip>
    jupyter                   1.0.0                    py27_0  
    jupyter-dashboards        0.5.2                     <pip>
    jupyter_client            4.2.1                    py27_0  
    jupyter_console           4.0.2                    py27_0  
    jupyter_core              4.1.0                    py27_0  
    libgdal                   1.11.2                        0  
    libgfortran               3.0                           0  
    libnetcdf                 4.3.3.1                       1  
    libpng                    1.6.17                        0  
    libsodium                 0.4.5                         0  
    libxml2                   2.9.2                         0  
    llvmlite                  0.5.0                    py27_0  
    logilab-common            1.0.1                     <pip>
    lxml                      3.4.4                    py27_0  
    mapnik                    0.1                       <pip>
    Markdown                  2.6.2                     <pip>
    matplotlib                1.4.3                np19py27_2  
    mistune                   0.5.1                    py27_1  
    mkl                       11.3.1                        0  
    mkl-rt                    11.1                         p0  
    mkl-service               1.0.0                   py27_p1  
    mklfft                    2.0                 np19py27_p0  
    MySQL-python              1.2.5                     <pip>
    nb_anacondacloud          1.2.0                    py27_0  
    nb_conda                  2.0.0                    py27_0  
    nb_conda_kernels          2.0.0                    py27_0  
    nbconvert                 4.0.0                    py27_0  
    nbformat                  4.0.0                    py27_0  
    nbpresent                 3.0.2                    py27_0  
    netcdf4                   1.1.9                np19py27_0  
    networkx                  1.9.1                    py27_0  
    nltk                      3.0.3                np19py27_0  
    nose                      1.3.7                     <pip>
    nose                      1.3.7                    py27_0  
    notebook                  4.2.2                    py27_0  
    notedown                  1.4.4                     <pip>
    numba                     0.19.1               np19py27_0  
    numbapro                  0.18.0              np19py27_p2  
    numbapro_cudalib          0.2                           0  
    numexpr                   2.4.3                np19py27_0  
    numpy                     1.11.0                    <pip>
    numpy                     1.9.2                    py27_0  
    oauthlib                  0.7.2                     <pip>
    odo                       0.3.2                np19py27_0  
    openblas                  0.2.14                        4  
    openpyxl                  1.8.5                    py27_0  
    openpyxl                  2.2.5                     <pip>
    openssl                   1.0.1k                        1  
    pandas                    0.16.2               np19py27_0  
    pandas                    0.18.1                    <pip>
    pandasql                  0.6.2                np19py27_0  
    pandasql                  0.6.3                     <pip>
    pandoc-attributes         0.1.7                     <pip>
    pandocfilters             1.2.4                     <pip>
    patchelf                  0.6                           0  
    path.py                   8.1.2                    py27_1  
    path.py                   8.2.1                     <pip>
    pcre                      8.31                          0  
    pexpect                   3.3                      py27_0  
    pickleshare               0.5                      py27_0  
    pillow                    2.8.2                    py27_0  
    Pillow                    2.9.0                     <pip>
    pip                       7.1.0                     <pip>
    pip                       8.1.1                     <pip>
    pip                       8.1.2                     <pip>
    pip                       8.1.2                    py27_0  
    pivottablejs              0.1.0                     <pip>
    plotly                    1.7.2                     <pip>
    ply                       3.6                      py27_0  
    prettyplotlib             0.1.7                     <pip>
    psutil                    3.0.1                     <pip>
    psycopg2                  2.6                      py27_1  
    ptyprocess                0.5                       <pip>
    py                        1.4.27                   py27_0  
    py                        1.4.30                    <pip>
    pyasn1                    0.1.8                     <pip>
    pycparser                 2.14                      <pip>
    pycparser                 2.14                     py27_0  
    pycurl                    7.19.5.1                 py27_2  
    pyflakes                  0.9.2                     <pip>
    pyflakes                  0.9.2                    py27_0  
    pygaarst                  0.0.1                     <pip>
    pylint                    1.4.4                     <pip>
    pymc                      2.3.4               np19py27_p0  [mkl]
    pyopenssl                 0.15.1                   py27_1  
    pyparsing                 2.0.3                    py27_0  
    pyproj                    1.9.4                     <pip>
    pyqt                      4.11.3                   py27_1  
    pysal                     1.6.0                np19py27_1  
    PySAL                     1.9.1                     <pip>
    pyshp                     1.2.3                     <pip>
    pystache                  0.5.4                     <pip>
    pytables                  3.2.0                np19py27_0  
    pytest                    2.7.1                    py27_0  
    pytest                    2.7.2                     <pip>
    python                    2.7.10                        0  
    python-dateutil           2.4.2                    py27_0  
    python-dateutil           2.5.3                     <pip>
    pytz                      2015.4                   py27_0  
    pytz                      2016.4                    <pip>
    pyyaml                    3.11                     py27_1  
    pyzmq                     14.7.0                   py27_0  
    qt                        4.8.6                         3  
    qtconsole                 4.0.1                    py27_0  
    rasterio                  0.24.1                    <pip>
    readline                  6.2                           2  
    requests                  2.7.0                    py27_0  
    requests-oauthlib         0.5.0                     <pip>
    rope                      0.10.2                    <pip>
    ruamel_yaml               0.11.14                  py27_0  
    scikit-image              0.11.3               np19py27_0  
    scikit-learn              0.16.1               np19py27_0  
    scipy                     0.15.1               np19py27_0  
    seaborn                   0.6.0                     <pip>
    setuptools                26.1.1                   py27_0  
    Shapely                   1.5.9                     <pip>
    simplegeneric             0.8.1                    py27_0  
    simplejson                3.7.3                     <pip>
    singledispatch            3.4.0.3                  py27_0  
    sip                       4.16.5                   py27_0  
    six                       1.10.0                    <pip>
    six                       1.9.0                    py27_0  
    snowballstemmer           1.2.0                    py27_0  
    snuggs                    1.3.1                     <pip>
    sockjs-tornado            1.0.1                    py27_0  
    Sphinx                    1.3.1                     <pip>
    sphinx                    1.3.1                    py27_0  
    sphinx-rtd-theme          0.1.8                     <pip>
    sphinx_rtd_theme          0.1.7                    py27_0  
    spyder                    2.3.5.2                   <pip>
    spyder                    2.3.5.2                  py27_0  
    spyder-app                2.3.5.2                  py27_0  
    sqlalchemy                1.0.5                    py27_0  
    SQLAlchemy                1.0.6                     <pip>
    sqlite                    3.13.0                        0  
    sqlparse                  0.1.14                   py27_0  
    sqlparse                  0.1.17                    <pip>
    sympy                     0.7.6                    py27_0  
    system                    5.8                           2  
    terminado                 0.5                      py27_0  
    theano                    0.7.0                np19py27_0  
    tk                        8.5.18                        0  
    toolz                     0.7.2                    py27_0  
    tornado                   4.2                      py27_0  
    tqdm                      3.4.0                     <pip>
    traitlets                 4.1.0                    py27_0  
    twitter                   1.17.0                    <pip>
    unicodecsv                0.13.0                    <pip>
    urbansim                  2.0.1                     <pip>
    version-information       1.0.3                     <pip>
    hdf4                      4.2.11                      232    vitale232
    websocket                 0.2.1                     <pip>
    werkzeug                  0.10.4                   py27_0  
    wheel                     0.29.0                   py27_0  
    xlrd                      0.9.3                    py27_0  
    XlsxWriter                0.7.3                     <pip>
    xlsxwriter                0.7.3                    py27_0  
    xlwt                      1.0.0                    py27_0  
    yaml                      0.1.6                         0  
    zeromq                    4.0.5                         0  
    zlib                      1.2.8                         3  



```python
#List of installed pip packages
!pip list
```

    abstract-rendering (0.5.1)
    affine (1.2.0)
    alabaster (0.7.6)
    anaconda-client (1.5.1)
    aniso8601 (1.1.0)
    argcomplete (0.8.9)
    arrow (0.5.4)
    astroid (1.3.6)
    astropy (1.0.3)
    Babel (1.3)
    backports-abc (0.4)
    backports.shutil-get-terminal-size (1.0.0)
    backports.ssl-match-hostname (3.4.0.2)
    basemap (1.0.7)
    bcolz (0.9.0)
    beautifulsoup4 (4.4.0)
    binstar (0.11.0)
    bitarray (0.8.1)
    blaze (0.8.0)
    blz (0.6.2)
    bokeh (0.9.0)
    boto (2.38.0)
    bottle (0.12.8)
    Bottleneck (1.0.0)
    bqplot (0.3.8)
    brewer2mpl (1.4.1)
    Cartopy (0.13.0)
    cdecimal (2.3)
    certifi (2015.4.28)
    cffi (1.1.2)
    click (4.0)
    cligj (0.2.0)
    clyent (0.3.4)
    colorama (0.3.3)
    conda (4.1.11)
    conda-build (1.12.1)
    conda-env (2.5.0a0)
    configobj (5.0.6)
    coverage (4.0.1)
    cryptography (0.9.1)
    Cython (0.22.1)
    cytoolz (0.7.3)
    datashape (0.4.5)
    decorator (3.4.2)
    descartes (1.0.1)
    docopt (0.6.2)
    docutils (0.12)
    enum (0.4.4)
    enum34 (1.0.4)
    fastcache (1.0.2)
    Fiona (1.5.1)
    Flask (0.10.1)
    Flask-RESTful (0.3.4)
    folium (0.1.6)
    funcsigs (0.4)
    functools32 (3.2.3.post1)
    futures (3.0.3)
    GDAL (2.0.0)
    geopandas (0.1.1)
    geopy (1.10.0)
    gevent (1.0.2)
    gevent-websocket (0.9.5)
    greenlet (0.4.7)
    grin (1.2.1)
    h5py (2.5.0)
    html5lib (0.999)
    hypothesis (3.1.1)
    idna (2.0)
    igraph (0.1.8)
    ipaddress (1.0.7)
    ipykernel (4.4.1)
    ipyparallel (5.0.1)
    ipython (4.2.0)
    IPython-Dashboard (0.1.5)
    ipython-genutils (0.1.0)
    ipywidgets (4.0.2)
    isodate (0.5.1)
    itsdangerous (0.24)
    jdcal (1.0)
    jedi (0.9.0)
    Jinja2 (2.7.3)
    jsonschema (2.5.1)
    jupyter (1.0.0)
    jupyter-client (4.2.1)
    jupyter-console (4.0.2)
    jupyter-core (4.1.0)
    jupyter-dashboards (0.5.2)
    llvmlite (0.5.0)
    logilab-common (1.0.1)
    lxml (3.4.4)
    mapnik (0.1)
    Markdown (2.6.2)
    MarkupSafe (0.23)
    matplotlib (1.4.3)
    mistune (0.5.1)
    mklfft (0.0.0)
    mock (1.0.1)
    multipledispatch (0.4.7)
    MySQL-python (1.2.5)
    nb-anacondacloud (1.2.0)
    nb-conda (2.0.0)
    nb-conda-kernels (2.0.0)
    nbconvert (4.0.0)
    nbformat (4.0.0)
    nbpresent (3.0.2)
    netCDF4 (1.1.9)
    networkx (1.9.1)
    nltk (3.0.3)
    nose (1.3.7)
    notebook (4.2.2)
    notedown (1.4.4)
    numba (0.19.1)
    numbapro (0.18.0)
    numexpr (2.4.3)
    numpy (1.11.0)
    oauthlib (0.7.2)
    odo (0.3.2)
    openpyxl (2.2.5)
    pandana (0.1.2)
    pandas (0.18.1)
    pandasql (0.6.3)
    pandoc-attributes (0.1.7)
    pandocfilters (1.2.4)
    path.py (8.2.1)
    patsy (0.3.0)
    pep8 (1.6.2)
    pexpect (3.3)
    pickleshare (0.5)
    Pillow (2.8.2)
    pip (8.1.2)
    pivottablejs (0.1.0)
    plotly (1.7.2)
    ply (3.6)
    prettyplotlib (0.1.7)
    prettytable (0.7.2)
    psutil (3.0.1)
    psycopg2 (2.6)
    ptyprocess (0.5)
    py (1.4.30)
    pyasn1 (0.1.8)
    pycosat (0.6.1)
    pycparser (2.14)
    pycrypto (2.6.1)
    pycurl (7.19.5.1)
    pyflakes (0.9.2)
    pygaarst (0.0.1)
    Pygments (2.0.2)
    pylint (1.4.4)
    pymc (2.3.4)
    pyOpenSSL (0.15.1)
    pyparsing (2.0.3)
    pyproj (1.9.4)
    PySAL (1.9.1)
    pyshp (1.2.3)
    pysptools (0.13.0)
    pystache (0.5.4)
    PyStretch (0.2.1)
    pytest (2.7.1)
    python-dateutil (2.5.3)
    pytz (2016.4)
    PyYAML (3.11)
    pyzmq (14.7.0)
    qtconsole (4.0.1)
    rasterio (0.24.1)
    rdflib (4.2.0)
    redis (2.10.3)
    requests (2.7.0)
    requests-oauthlib (0.5.0)
    rise (4.0.0b1)
    rope (0.10.2)
    rpy2 (2.5.6)
    ruamel-yaml (-VERSION)
    runipy (0.1.3)
    scikit-image (0.11.3)
    scikit-learn (0.16.1)
    scipy (0.15.1)
    seaborn (0.6.0)
    setuptools (26.1.1)
    Shapely (1.5.9)
    simplegeneric (0.8.1)
    simplejson (3.7.3)
    singledispatch (3.4.0.3)
    six (1.10.0)
    snowballstemmer (1.2.0)
    snuggs (1.3.1)
    sockjs-tornado (1.0.1)
    SPARQLWrapper (1.6.4)
    spectral (0.16.1)
    Sphinx (1.3.1)
    sphinx-rtd-theme (0.1.8)
    spyder (2.3.5.2)
    SQLAlchemy (1.0.5)
    sqlparse (0.1.17)
    statsmodels (0.6.1)
    sympy (0.7.6)
    tables (3.2.0)
    tabulate (0.7.5)
    terminado (0.5)
    Theano (0.7.0)
    toolz (0.7.2)
    tornado (4.2)
    tqdm (3.4.0)
    traitlets (4.1.0)
    tweepy (2.3.0)
    twitter (1.17.0)
    ujson (1.33)
    unicodecsv (0.13.0)
    urbansim (2.0.1)
    version-information (1.0.3)
    websocket (0.2.1)
    Werkzeug (0.10.4)
    wheel (0.29.0)
    xlrd (0.9.3)
    XlsxWriter (0.7.3)
    xlwt (1.0.0)


## Running dynamic presentations

You need to install the [RISE Ipython Library](https://github.com/damianavila/RISE) from [Damián Avila](https://github.com/damianavila) for dynamic presentations

## About me

 

![It's all about me - details about Anthony Beck](https://dl.dropboxusercontent.com/u/393477/ImageBank/Geolytics_ARB_Banner.png)

* Honorary Research Fellow, University of Nottingham: [orcid](http://orcid.org/0000-0002-2991-811X)
* Director, Geolytics Limited - A spatial data analytics consultancy

## About this presentation

* [Available on GitHub](https://github.com/AntArch/Presentations_Github/tree/master/20151008_OpenGeo_Reuse_under_licence) - https://github.com/AntArch/Presentations_Github/
* [Fully referenced PDF](https://github.com/AntArch/Presentations_Github/blob/master/201609_UtilityAddresses_Presentation/201609_UtilityAddresses_Presentation.pdf)


\newpage

To convert and run this as a static presentation run the following command:


```python
# Notes don't show in a python3 environment

!jupyter nbconvert 201609_UtilityAddresses_Presentation.ipynb --to slides --post serve


```

    /home/arb/LocalPython/Anaconda27/anaconda/lib/python2.7/site-packages/IPython/nbconvert.py:13: ShimWarning: The `IPython.nbconvert` package has been deprecated. You should import from nbconvert instead.
      "You should import from nbconvert instead.", ShimWarning)
    [NbConvertApp] Converting notebook 201609_UtilityAddresses_Presentation.ipynb to slides
    [NbConvertApp] Writing 320863 bytes to 201609_UtilityAddresses_Presentation.slides.html
    [NbConvertApp] Redirecting reveal.js requests to https://cdn.jsdelivr.net/reveal.js/2.6.2
    Serving your slides at http://127.0.0.1:8000/201609_UtilityAddresses_Presentation.slides.html
    Use Control-C to stop this server
    [1:1:0904/143137:ERROR:chrome_content_client.cc(335)] Failed to locate and load the component updated flash plugin.
    [27077:27077:0904/143137:ERROR:chrome_content_client.cc(335)] Failed to locate and load the component updated flash plugin.
    Created new window in existing browser session.
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 2.07ms
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 1.61ms
    WARNING:tornado.access:404 GET /favicon.ico (127.0.0.1) 0.84ms
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 0.94ms
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 0.64ms
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 0.97ms
    WARNING:tornado.access:404 GET /custom.css (127.0.0.1) 0.98ms


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

# Addresses

![@kaye_map_2012](https://farm9.staticflickr.com/8334/8076658843_bb93c499c9_z_d.jpg)

are part of the fabric of everyday life


\newpage

# Addresses

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Flag_of_UPU.svg/640px-Flag_of_UPU.svg.png)

Have economic and commercial impact

\newpage

# Addresses

![@appelo_governance_2010](https://farm6.staticflickr.com/5204/5201270923_f02844bb41_z_d.jpg)

Support governance and democracy

* Without an address, it is harder for individuals to register as legal residents. 
* They are *not citizens* and are excluded from:
	* public services 
	* formal institutions.
* This impacts on democracy. 



\newpage

# Addresses

![@beck_social_integration_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Stufen_Schulischer_Integration_enGB.svg/500px-Stufen_Schulischer_Integration_enGB.svg.png)

Support Legal and Social integration

* Formal versus Informal
* Barring individuals and businesses from systems:
	* financial
	* legal
	* government
	* ....


\newpage

# Addresses 

bridge gaps - provide the link between ***people*** and ***place***

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/AdressesProvidePeopleWithPlace.png)

\newpage

# Utility Addresses


## In the beginning ...... was the ledger

![@ledger_en_beck_2016](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Everton_1933_FA_Cup_team_selection_ledger.JPG/681px-Everton_1933_FA_Cup_team_selection_ledger.JPG)



\newpage

## Bespoke digital addresses 

* Digitisation and data entry to create a bespoke Address Database - 
	* Fit for UU's operational purpose
	* Making utilities a key *owner* of address data
		* Subject to IP against PAF matching

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/AMS_InDetail.png)



\newpage

## Policy mandates

Open Water - A shared view of addresses requiring a new addressing paradigm - Address Base Premium?

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/OpenWater.png)


\newpage


# Utility addressing:



* Postal delivery (Billing)
	* Services and Billing to properties within the extent of the UU operational area
	* Billing to customers outside the extent of UU operational area
* Asset/Facilities Management (infrastructure)
	* Premises
		* But utilties manage different assets to Local Authorities
		* is an address the best way to manage a geo-located asset? 
* Bill calculation
	* Cross referencing Vaulation Office and other detals.

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/AMS_InDetail.png)

\newpage



. . . . 

**It's not just postal addressing**

. . . . 

**Address credibility is critical**

. . . . 

Utilities see the full life-cycle of an address - especially the birth and death

\newpage

##  asset management

* UU manage assets and facilities

> According to ABP a Waste Water facility is neither a postal address or a non-postal address. 

Really? Is it having an existential crisis?

![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Utility_trench_in_Bwy_%40_42_St_jeh.jpg/576px-Utility_trench_in_Bwy_%40_42_St_jeh.jpg)


\newpage

##  A connected spatial network

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/UU_SPA_CONCEPTUAL.png)

\newpage

##  Serving customers who operate **somewhere**

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/UU_ElegiblePremiseConcepts.png)

* UU serve customers located in 
	* Buildings
	* Factories
	* Houses
	* Fields


\newpage

##  Serving customers who operate **anywhere**

![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Colling_Trough_Collingtree_UK_2007.JPG/597px-Colling_Trough_Collingtree_UK_2007.JPG)



\newpage

# Utility addressing issues


* Addresses are a pain
	* Assets as locations
	* Services as locatons
	* People at locations

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/AMS_InDetail.png)

\newpage

# Issues: addresses = postal address.

* Is *Postal* a constraining legacy?
* Is *address* a useful term? 

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/Mono_pensador.jpg)



\newpage

# Issues: Do formal *addresses* actually help utilities?

* External addresses (ABP for example) are another product(s) to manage
	* which may not fit the real business need
	* which may not have full customer or geographic coverage
    
![](https://upload.wikimedia.org/wikipedia/commons/0/0d/Mono_pensador.jpg)

\newpage


# What is an address?

##  Address abstraction

* Address did not spring fully formed into existance. 
* They are used globally
	* but developed nationally
	* and for different reasons

![@AddressAbstraction_beck_2016](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Postal_Address_Abstraction.svg/1024px-Postal_Address_Abstraction.svg.png)

\newpage

##  Royal Mail - postal delivery

![](https://dl.dropboxusercontent.com/u/393477/1Spatial/1S_ADP_creating_AP_DP.gif)



In a postal system:

* a *Delivery Point* (DP) is a single mailbox or other place at which mail is delivered. 
    * a single DP may be associated with multiple addresses 
* An *Access Point* provides logistical detail.

The postal challenge is to solve the last 100 meters. In such a scenario the *post person* is critical. 

DPs were collected by the Royal Mail for their operational activities and sold under licence as the *Postal Address File* (PAF). PAF is built around the 8-character *Unique Delivery Point Reference Number* (UDPRN). The problem with PAF is that the spatial context is not incorporated into the product. Delivery points are decoupled from their spatial context - a delivery point with a spatial context should provide the clear location of the point of delivery (a door in a house, a post-room at an office etc.).

\newpage

##  LLPG - asset management

![[Borough of Harrown LLPG schematic](https://www.ggpsystems.co.uk/wp-content/uploads/2010/12/LBH-LLPG-System-flow-Diagram-300x211.png)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/LBH-LLPG-System-flow-Diagram.png)



An LLPG (Local Land and Property Gazetteer) is a collection of address and location data created by a local authority. 

It is an Asset/Facilities Management tool to support public service delivery:

* Local Authority
* Police
* Fire
* Ambulance

It incorporates:

* Non postal addresses (i.e. something that the Royal Mail wouldn't deliver post to)

* a 12-digit Unique Property Reference Number for every building and plot of land
* National Street Gazetteer

Prior to the initialization of the LLPGs, local authorities would have different address data held across different departments and the purpose of the Local Land and Property Gazetteers was to rationalize the data, so that a property or a particular plot of land is referred to as the same thing, even if they do have different names.

\newpage

##  Addresses as assets?

![[Post box](http://joncruddas.org.uk/sites/joncruddas.org.uk/files/styles/large/public/field/image/post-box.jpg?itok=ECnzLyhZ)](http://joncruddas.org.uk/sites/joncruddas.org.uk/files/styles/large/public/field/image/post-box.jpg?itok=ECnzLyhZ)

* So what makes the following 'non-postal' *facilities*  addresses:
	* Chimney
	* Post box - which is clearly having a letter delivered ;-)
	* Electricity sub-station
* Context is critical
    * So why is a waste-water facility not an address in ABP (when an Electricity sub-station is)? 
        * Because it is not *of interest* to a council and the Royal Mail have never been asked to deliver mail to it.

\newpage

##  Korea: The Jibeon system - taxation

![after (@_addressing_2012, p.57)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/JibeonAddressingUPU_pg57.png)



* Until recently, the Republic of Korea (Korea) has used land parcel numbers ( jibeon) to identify unique locations. 
    * These parcel numbers were assigned chronologically according to date of construction and without reference to the street where they were located. 
    * This meant that adjacent buildings did not necessarily follow a sequential numbering system.
* This system was initially used to identify land for census purposes and to levy taxes. 
* In addition, until the launch of the new addressing system, the jibeon was also used to identify locations (i.e. a physical address). 

\newpage

##  World Bank - social improvement

![@world_bank_address_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/World_Bank_Recommended_Address_Infrastucture.svg/640px-World_Bank_Recommended_Address_Infrastucture.svg.png)



The World Bank has taken a *street addressing* view-point (@_addressing_2012, p.57). This requires up-to-date mapping and bureacracy (to deliver a street gazetteer and to provide the street infrastructure (furniture)). However, (@_addressing_2012, p.44) demonstrates that this is a cumbersome process with a number of issues, not the least:

* Urban bias
* Cost of infrastucture development
* Lack of community involvment

\newpage

##  Denmark: An addressing commons with impact

![after @lind2008addresses](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/Lind_AddressesAsAnInfrastructureDenmark_Before.png)

![after @lind2008addresses](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/Lind_AddressesAsAnInfrastructureDenmark_After.png)

\newpage

##  Denmark: An addressing commons with impact

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

A credible service providing a mutlitude of efficiencies (@_addressing_2012, pp.50 - 54)



\newpage


# UK Addressing

##  Geoplace - Formal

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

##  The AddressBase Family

![Ordnance Survey](http://demos.ordnancesurvey.co.uk/public/demos/products/AddressBase/images/database_3_0.jpg)



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

##  Address lifecycle

![[addressbase products user guide (p. 9)](https://www.europa.uk.com/resources/os/addressbase-products-user-guide.pdf)](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/ABP_Lifecycle.png)



* This ability to maintain an overview of the lifecycle of address and property status means the AddressBase Premium has introduced new potential use cases. 
* This has seen companies incorporating AddressBase Premium into their business systems to replace PAF or bespoke addressing frameworks - in theory the ability to authoritatively access the address lifecycle provides greater certainty for a number of business operations. 

* At *United Utilites* (UU) AddressBase Premium is replacing a multitude of bespoke and PAF based addressing products. 


\newpage

##  [Open National Address Gazetteer](https://www.gov.uk/government/publications/an-open-national-address-gazetteer) - *informal?*

The *Department for Business, Innovation & Skills* (BIS) on the need for an [Open National Address Gazetteer](https://www.gov.uk/government/publications/an-open-national-address-gazetteer) commissioned a review of *open addressing* which was published January 2014. 

. . . . . 

It recommended:

* the UK Government commission an 'open' addressing product based on a variation of the 'freemium' model 
	* data owners elect to release a basic ('Lite') product as Open Data that leaves higher value products to be licensed

. . . . . 

AddressBase Lite was proposed with an annual release cycle. Critically this contains the UPRN which could be be key for product interoperability.
* This would allow the creation of a shared interoperable address spine along the lines of the Denmark model

\newpage

##  Open NAG - [*'Responses received'*](https://www.gov.uk/government/publications/an-open-national-address-gazetteer) April 2014

With the exception of the PAF advisory board and Royal Mail there was support for the BIS review across the respondants with some notable calls for the *Totally Open* option (particularly from those organisations who are not part of the Public Sector Mapping Agreement) and that the UPRN should be released under an open data licence (as a core reference data set that encourages product interoperability).

. . . . . 

A number of quotes have been selected below:

\newpage

##  Addresses as an Open Core Reference

>....Address data and specific locations attached to them **are part of Core Reference data sets recognised by government as a key component of our National Information Infrastructure** (as long argued by APPSI). The report published by BIS gives us **a chance to democratise access to addressing data** and meet many of the Government’s avowed intentions. We urge acceptance of Option 6 *(freemium)* or 7 *(an independent open data product)*. 

**David Rhind *Chair of the Advisory Panel on Public Sector Information* **

>....**Freely available data are much more likely to be adopted** by users and embedded in operational systems. **A national register, free at the point of delivery will undoubtedly help in joining up services, increasing efficiency and reducing duplication**. 

**Office of National Statistics**

\newpage

##  Monopoly rent exploitation

>... we expressed concern that, for almost all other potential customers (non-public sector), **the prices are prohibitive**, and appear designed to protect OS’s existing policy of setting high prices for a small captive market, **extracting monopoly rent**. 

**Keith Dugmore *Director, DUG* **

\newpage

##  The benefit of current credible addresses

>**The problem of out-of-date addresses is a very significant commercial cost** for the whole of the UK and is also arguably underplayed in the report. 

**Individual Respondent 3**

\newpage

##  Licences

>Whatever licence the data is available under, **it must permit the data to be combined with other open data and then re-published**. ... The [Open Government Licence](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) fulfils this criteria, but it should be noted that the [OS OpenData Licence](http://www.ordnancesurvey.co.uk/docs/licences/os-opendata-licence.pdf) (enforced by OS on it's OS OpenData products, and via the PSMA) does not. The use of the latter would represent a significant restriction on down-stream data use, and so should be avoided. 

**Individual Respondent 6**




\newpage

# Taking Stock

##  Addresses are heterogeneous

![@world_addressing_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Addressing_around_the_world.svg/640px-Addressing_around_the_world.svg.png)

In terms of:

* What they mean
* What they are used for
* Who uses them
* How they are accessed

\newpage

##  Assets can have addresses

So - anything can have an address (the *Internet of Things*)

![[Post box](http://joncruddas.org.uk/sites/joncruddas.org.uk/files/styles/large/public/field/image/post-box.jpg?itok=ECnzLyhZ)](http://joncruddas.org.uk/sites/joncruddas.org.uk/files/styles/large/public/field/image/post-box.jpg?itok=ECnzLyhZ)

\newpage

##  National data silos

![@IslandsOfData_en_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Islands_Of_Data.svg/636px-Islands_Of_Data.svg.png)

They have been created to solve national issues. 

No unifying semantics

\newpage

##  

![@IncompatibilitiesAndLicenceClauses_en_beck_2016](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Incompatibilities_And_Licence_Clauses.svg/989px-Incompatibilities_And_Licence_Clauses.svg.png)

\newpage

##  Addresses are bureaucratic and costly

![@stamp_schnettelker_2013](https://farm3.staticflickr.com/2819/9786091286_e85fd01bb8_z_d.jpg)

Severely protracted when formal/informal issues are encountered.

\newpage

##  Addresses can be opaque

![@processing_transparency_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Processing_transparency_between_open_and_closed_systems.svg/630px-Processing_transparency_between_open_and_closed_systems.svg.png)

**transparent and reproducible?**

\newpage

##  Addresses are of global significance

![@services_products_Gray_2011](https://farm7.staticflickr.com/6213/6296605302_9745b5e72e_z_d.jpg)

\newpage

##  Addresses are ripe for disruption

![@earth_egg_rain_2007](https://farm3.staticflickr.com/2159/2047910540_82620d9481_z_d.jpg?zz=1)



\newpage


# Address Disruption

##  Formal versus informal

![@formalinformal_beck_2016](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/FormalVersusInformalKnowledgeRepositoriesWithODI.png)

\newpage

##  Technology

Streets are so last century.....

![@world_bank_address_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/World_Bank_Recommended_Address_Infrastucture.svg/640px-World_Bank_Recommended_Address_Infrastucture.svg.png)

* Ubiquitous GPS/GNSS
* Structured crowdsourced geo-enabled content (wikipedia, OSM)

\newpage

##  Interoperability

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/Plug_interoperability.svg.png)

* Will the semantic web provide address interoperabilty?

* between addressing systems
* to incorporate additional data
    * VOA
    * ETC

\newpage

##  Globalisation

![@linked_data_staveren_2013](https://farm8.staticflickr.com/7374/9965173654_7bf862d89d_z_d.jpg)

* Addressing is a **core reference geography**
* Global brands will demand (or invoke) consistent global addressing
* How will licences impact on this?

\newpage

# A new global address paradigm?  

* [Amazon drone delivery in the UK requires](https://www.theguardian.com/technology/2016/jul/25/amazon-to-test-drone-delivery-uk-government)
	* A new view over addressing complements streets and buildings but is geo-coded at source
	* and supports accurate delivery throughout the delivery chain using a global referencing system.

Is there a universal approach which allows all avenues to be satisfied?

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/Guardian_Amazon_drone.png)


\newpage

##  How might this look?

.
.

Requirements for a Global Address Framework

.
.

\newpage

##  WGS84 algorithmic address minting

![@minting_addresses_2009](https://farm3.staticflickr.com/2432/3832442378_bf76a81b5d_d.jpg)

**A global addressing framework needs to be transparent and reproducible.**

**A global addressing framework should be based on a spatial reference system.**

**A global addressing framework needs to be lightweight and cheap so it can be implemented in a timely manner.**

\newpage

##  Small footprint

![@small_footprints_terwolbeck_2012](https://farm8.staticflickr.com/7185/6988489897_282270cfd5_z_d.jpg)

**Ubiquitous access across platforms.**

**No dependency on internet access.**

\newpage

##  Short/memorable

![@mnemonics_munroe_nd](http://imgs.xkcd.com/comics/mnemonics.png)

\newpage

##  Self checking 

![@parity_levine_2014](https://farm6.staticflickr.com/5576/14117894364_a3715fdfce_z_d.jpg)

**Improving validity and credibility of downstream business processes.**

\newpage

##  Unlimited spatial recording

![@geodesic_grid_petersen_2007](https://upload.wikimedia.org/wikipedia/en/thumb/f/fd/Geodesic_Grid_%28ISEA3H%29_illustrated.png/1024px-Geodesic_Grid_%28ISEA3H%29_illustrated.png)

* What are the spatial requirements for the range of addressing options?
    * [Manila has a population density of 42,857 people per square km](http://en.wikipedia.org/wiki/List_of_cities_proper_by_population_density). 
    * [Map Kibera](http://mapkibera.org/) and OSM has revolutionised service delivery in Kibera (Kenya). 
        * Address Kibera could do the same thing for citizenship.

**A global addressing framework should meet the needs of the rural, urban, formal and informal communities equally.**

\newpage

##  Open and interoperable

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/PromotingInteroperability.png)

\newpage

##  Open and interoperable

> the lack of a consistent and transparent legal and policy framework for sharing spatial data continues to be an additional roadblock.

@pomfret_spatial_2010

**A global addressing framework should be open or available with as few barriers as possible.**

\newpage

##  Indoor use and 3D

![@bim_arup_2013](http://architect-bim.co.uk/wp-content/uploads/2013/03/Arup-steel-ec-fame.jpg)

Incorporating wifi-triangulation - *individual room* addressing and navigation.

Seamless integration with BIM and CityGML.

*Addressing isn't only about buildings - think about the Internet of Things*

\newpage

##  Inherent geo-statistical aggregation (spatially scalable)

![@geodesic_grid_petersen_2007](http://upload.wikimedia.org/wikipedia/en/thumb/f/fd/Geodesic_Grid_%28ISEA3H%29_illustrated.png/640px-Geodesic_Grid_%28ISEA3H%29_illustrated.png)

GIS free multi-scale analysis and reporting during disaster scenarios.

\newpage

# Utility address concepts


* A means of communicating location to third parties in a way **they** understand.
	* Delivery
	* Contract engineer
	* Incident reporting
* Hence, addresses are all about sharing
	* We need to *buy into* disambiguating stakeholder semantics
        * Democratise the infrastructure
        * Democratise re-use
* Everything is mediated by a human in the information exchange
	* Everyone has their own semantics
	* Formal and vernacular geographies

\newpage

##  Addresses mediate space

In business systems addresses are bridge a between technology stacks and social systems.  



![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/UU_Addressing_Concept.png)



\newpage

##  Addresses mediate space

In business systems addresses are bridge a between technology stacks and social systems.  



![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/UU_Addressing_Concept_rosetta_stone.png)



* Challenges
	* find an unambiguous way to encode these different address types across the enterprise (and/or as part of an open initiative)
	* find ways to dynamically transform these address so that each end-user community get the most appropriate address be they:
		* formal addresses
		* vernacular (informal) addresses 
		* Postal address
		* Asset location

\newpage

* Most people in the UK think of an address as a *postal address*
	* This is a mindset we should be trying to break
	* A delivery address is only one facet to an address
* What do addresses enable
	* Services
		* Postal services
		* Utility services
		* etc
	* Routing
		* Vehicle navigation
		* People navigation
	* Asset/Infrastructure management
	* Information integration
		* Lifecycle
		* Geodemographics
* Hence, addressing information covers a range of requirements:
	* Semantic
	* GIS
	* Database
* Challenges
	* find an unambiguous way to encode these different address types across the enterprise (and/or as part of an open initiative)
	* find ways to dynamically transform these address so that each end-user community get the most appropriate address be they:
		* formal addresses
		* vernacular (informal) addresses 
		* Postal address
		* Asset location



\newpage

In terms of assets two things spring to mind - 

1. we no longer need streets and buildings to provide an address. 
    * GNSS already does this globally. 
    * The challenge is to translate GNSS into something appropriate for other services
1. The Access point/Delivery point metaphor used by Royal Mail may be important for traction
    * solving the last 100m problem (or location of local drone delivery depot)

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/Guardian_Amazon_drone.png)

\newpage


# Current utility addressing?

##  A shared view over addressing?

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ForAddresses/UU_AMS_AND_ABP_relationships.png)

\newpage

##  A shared view over addressing?

Not really....

* ABP isn’t a silver bullet
	* Subset of required ‘formal - delivery’ addresses
	* Mis-match in terms of assets
		* Why does a sewage works not have an address when a post-box does?
	* Not plug and play
	* Lag in the system - the lifecycle feedback does not have credibility for time critical applications.
	* The co-ordinating spine is not freely available (under a permissive licence)
	* Inset areas - an aglomoration of 'addresses'
	* VOA link is a cludge

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/Mono_pensador.jpg)



\newpage

##  Addresses should mediate systems

* Bridge the gap between a building focussed 2d view of the world and the 3d world in which we inhabit. 
* Harmonise the edge cases relationships between UPRNs and VOAs

![](https://upload.wikimedia.org/wikipedia/commons/0/0d/Mono_pensador.jpg)

\newpage

##  Issues about ABP

* Users over a barrel
	* Needed to buy ABP as AL2 was being removed
* Data model change
	* a hostage to someone else's data model
* Lifecycle benefit not being realised (at least not for utilities)
    * Altough utilities have a significant value add
* Update frequency
* Different view of property hierarchy
* 2d and 3d metaphors against VOA
	* a better 2.5 view of the world would be appreciated.
* Licences do not encourage re-use and innovation




\newpage

##  This begs the question

> Why should utilities replace a functional bespoke address system with an address framework (ABP) that does not meet all their business requirements? 

This creates a paradox when products like AddressBase are stipulated in Government policy documents (such as OpenWater)

How can this gap be bridged? Can *open addresses* help?

**Addresses need to be fit-for-purpose for the end user**


\newpage

#  Future Addressing



##  What do Utilities need from an Open Address infrastructure

> Ant Beck will talk about how addresses are employed within United Utilities: from bespoke addressing, to the current implementation of Geoplace’s Address Base. 

>**The current approach to addressing hinders effective market activities so consideration is given to how Open approaches can disrupt the addressing landscape and improve utility services.**

* Should this simply emulate Address Base Premium?
    * No
* Like Denmark should it exploit technological developments to be:
	* More robust
	* Improve use case
	* More flexible


#  Future Addressing



##  What do Utilities need from an Open Address infrastructure

* Should it embrace technological development to make operational activities more efficient
	* Use disruptive technologies to facilitate geo-coded addressing of assets in a flexible and credible manner
* How can such an infrastructure interoperate with other formal and informal sources to provide benefits
* What licence would a service be under.
	* OS licence? -**No - it is restrictive**
    * The point is to encourage:
        * adoption 
        * engagement
        * re-use

> We would like to see an *open address infrastructure* in the UK **provide a platform for 21st Century addressing**

> It should **not simply aim to emulate ABP** - there are other use cases


\newpage

##  What can Utilities bring to Open Addresses

* A credible publisher of addressing updates under open licences providing:
    * additional content
    * improved lifecycle information
    * expanded use cases
    * improving confidence and credibility
* Critical lifecycle data updates 
    * potentially faster than local government (lag is critical to some users).


\newpage

##  What can Open Addresses bring to Utilities

* Fill the gap of formal and informal addresses
	* But share a common reference Spine
		* UPRN?
		* But what about the 3d world
* Add value
	* Link to different geoaddressing paradigm
        * W3W
        * GeoHash
        * etc.
	* Linked data?
	* Property life-cycle?
	* Spatially consistent
	* Crowd enhanced
* Service innovation
    * enhanced business intelligence from shared knowledge
	* geo-demographics protecting the disenfranchised
		* who are our sensitive customers - what are their needs?

\newpage

# Final thoughts

Utilities have the potential to be:

* Key consumers of open addressing data
* Key providers of open addressing content

**United Utilities would like to help frame this debate and be part of any solution.**

\newpage

# References


```python

```
