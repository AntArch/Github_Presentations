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

```{.python .input  n=2}
from IPython.display import YouTubeVideo
YouTubeVideo('F4rFuIb1Ie4')
```

```{.json .output n=2}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"400\"\n            height=\"300\"\n            src=\"https://www.youtube.com/embed/F4rFuIb1Ie4\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.YouTubeVideo at 0x7f694015ec18>"
  },
  "execution_count": 2,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

```{.python .input  n=34}
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

```{.json .output n=34}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "ipython nbconvert --to markdown 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb\n"
 },
 {
  "data": {
   "text/plain": "0"
  },
  "execution_count": 34,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

## The environment

In order to replicate my environment you need to know what I have installed!

### Set up watermark

This describes the versions of software used during the creation.

Please note that critical libraries can also be watermarked as follows:

```python
%watermark -v -m -p numpy,scipy
```

```{.python .input  n=3}
%install_ext https://raw.githubusercontent.com/rasbt/python_reference/master/ipython_magic/watermark.py
%load_ext watermark

```

```{.json .output n=3}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "Installed watermark.py. To use it, type:\n  %load_ext watermark\n"
 },
 {
  "name": "stderr",
  "output_type": "stream",
  "text": "/home/arb/LocalInstalls/anaconda3/lib/python3.5/site-packages/IPython/core/magics/extension.py:47: UserWarning: %install_ext` is deprecated, please distribute your extension(s)as a python packages.\n  \"as a python packages.\", UserWarning)\n"
 }
]
```

```{.python .input  n=4}
%watermark -a "Anthony Beck"  -d -v -m -g
```

```{.json .output n=4}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "Anthony Beck 24/01/2016 \n\nCPython 3.5.1\nIPython 4.0.2\n\ncompiler   : GCC 4.4.7 20120313 (Red Hat 4.4.7-1)\nsystem     : Linux\nrelease    : 3.19.0-32-generic\nmachine    : x86_64\nprocessor  : x86_64\nCPU cores  : 4\ninterpreter: 64bit\nGit hash   : \n"
 }
]
```

```{.python .input  n=5}
#List of installed conda packages
!conda list
```

```{.json .output n=5}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "# packages in environment at /home/arb/LocalInstalls/anaconda3:\n#\n_license                  1.1                      py35_1    defaults\nabstract-rendering        0.5.1               np110py35_0    defaults\naccelerate                2.0                np110py35_p0    defaults\naccelerate_cudalib        2.0                           0    defaults\naffine                    1.2.0                    py35_0    https://conda.binstar.org/ioos/linux-64/affine-1.2.0-py35_0.tar.bz2\nalabaster                 0.7.6                    py35_0    defaults\nanaconda                  2.4.1               np110py35_0    defaults\nanaconda-client           1.2.1                    py35_0    defaults\nargcomplete               1.0.0                    py35_1    defaults\nastropy                   1.1.1               np110py35_0    defaults\nbabel                     2.1.1                    py35_0    defaults\nbasemap                   1.0.7               np110py35_0    defaults\nbeautifulsoup4            4.4.1                    py35_0    defaults\nbitarray                  0.8.1                    py35_0    defaults\nblaze                     0.9.0                     <pip>\nblaze-core                0.9.0                    py35_0    defaults\nbokeh                     0.11.0                   py35_1    defaults\nboto                      2.38.0                   py35_0    defaults\nbottleneck                1.0.0               np110py35_0    defaults\ncffi                      1.2.1                    py35_0    defaults\nclick                     4.1                      py35_0    defaults\nclick-plugins             1.0.2                    py35_0    https://conda.binstar.org/ioos/linux-64/click-plugins-1.0.2-py35_0.tar.bz2\ncligj                     0.2.0                    py35_0    defaults\nclyent                    1.2.0                    py35_0    defaults\ncolorama                  0.3.3                    py35_0    defaults\ncolorlover                0.2.1                     <pip>\nconda                     3.19.0                   py35_0    defaults\nconda-build               1.18.2                   py35_0    defaults\nconda-env                 2.4.5                    py35_0    defaults\nconfigobj                 5.0.6                    py35_0    defaults\ncryptography              1.0.2                    py35_0    defaults\ncudatoolkit               7.0                           1    defaults\ncufflinks                 0.7.1                     <pip>\ncurl                      7.43.0                        1    defaults\ncycler                    0.9.0                    py35_0    defaults\ncython                    0.23.4                   py35_0    defaults\ncytoolz                   0.7.4                    py35_0    defaults\ndatashape                 0.5.0                    py35_0    defaults\ndecorator                 4.0.6                    py35_0    defaults\ndescartes                 1.0.1                    py35_0    https://conda.binstar.org/ioos/linux-64/descartes-1.0.1-py35_0.tar.bz2\ndocutils                  0.12                     py35_0    defaults\ndynd                      9b63882                   <pip>\ndynd-python               0.7.0                    py35_0    defaults\net-xmlfile                1.0.1                     <pip>\net_xmlfile                1.0.1                    py35_0    defaults\nfastcache                 1.0.2                    py35_0    defaults\nfiona                     1.6.0               np110py35_0    defaults\nflask                     0.10.1                   py35_1    defaults\nfontconfig                2.11.1                        5    defaults\nfreetype                  2.5.5                         0    defaults\nfuncsigs                  0.4                      py35_0    defaults\ngdal                      2.0.0                    py35_1    defaults\ngeos                      3.3.3                         0    defaults\ngreenlet                  0.4.9                    py35_0    defaults\nh5py                      2.5.0               np110py35_4    defaults\nhdf4                      4.2.11                        0    defaults\nhdf5                      1.8.15.1                      2    defaults\nhtml5lib                  0.9999999                 <pip>\nidna                      2.0                      py35_0    defaults\niopro                     1.7.2              np110py35_p0    defaults\nipykernel                 4.2.2                    py35_0    defaults\nipython                   4.0.2                    py35_0    defaults\nipython-genutils          0.1.0                     <pip>\nipython-notebook          4.0.4                    py35_0    defaults\nipython-qtconsole         4.0.1                    py35_0    defaults\nipython_genutils          0.1.0                    py35_0    defaults\nipywidgets                4.1.1                    py35_0    defaults\nitsdangerous              0.24                     py35_0    defaults\njbig                      2.1                           0    defaults\njdcal                     1.2                      py35_0    defaults\njedi                      0.9.0                    py35_0    defaults\njinja2                    2.8                      py35_0    defaults\njpeg                      8d                            0    defaults\njsonschema                2.4.0                    py35_0    defaults\njupyter                   1.0.0                    py35_1    defaults\njupyter-client            4.1.1                     <pip>\njupyter-console           4.1.0                     <pip>\njupyter-core              4.0.6                     <pip>\njupyter_client            4.1.1                    py35_0    defaults\njupyter_console           4.1.0                    py35_0    defaults\njupyter_core              4.0.6                    py35_0    defaults\nkealib                    1.4.5                         0    defaults\nkrb5                      1.13.2                        0    defaults\nlibdynd                   0.7.0                         0    defaults\nlibffi                    3.0.13                        0    defaults\nlibgdal                   2.0.0                         1    defaults\nlibgfortran               1.0                           0    defaults\nlibnetcdf                 4.3.3.1                       1    defaults\nlibpng                    1.6.17                        0    defaults\nlibsodium                 1.0.3                         0    defaults\nlibtiff                   4.0.6                         1    defaults\nlibxml2                   2.9.2                         0    defaults\nlibxslt                   1.1.28                        0    defaults\nllvmlite                  0.8.0                    py35_0    defaults\nlxml                      3.5.0                    py35_0    defaults\nmarkupsafe                0.23                     py35_0    defaults\nmatplotlib                1.5.1               np110py35_0    defaults\nmistune                   0.7.1                    py35_0    defaults\nmkl                       11.1               np110py35_p1    defaults\nmkl-rt                    11.1                         p0    defaults\nmkl-service               1.1.0                   py35_p0    defaults\nmock                      1.3.0                    py35_0    defaults\nmultipledispatch          0.4.8                    py35_0    defaults\nnbconvert                 4.1.0                    py35_0    defaults\nnbformat                  4.0.1                    py35_0    defaults\nnetworkx                  1.10                     py35_0    defaults\nnltk                      3.1                      py35_0    defaults\nnose                      1.3.7                    py35_0    defaults\nnotebook                  4.1.0                    py35_0    defaults\nnumba                     0.22.1              np110py35_0    defaults\nnumbapro                  0.22.1                  py35_p0    defaults\nnumexpr                   2.4.4              np110py35_p0  [mkl]  defaults\nnumpy                     1.10.2                  py35_p0  [mkl]  defaults\nodo                       0.4.0                    py35_0    defaults\nopenblas                  0.2.14                        3    defaults\nopenjpeg                  2.1.0                         0    https://conda.binstar.org/ioos/linux-64/openjpeg-2.1.0-0.tar.bz2\nopenpyxl                  2.3.2                    py35_0    defaults\nopenssl                   1.0.2e                        0    defaults\nowslib                    0.10.3                   py35_0    https://conda.binstar.org/ioos/linux-64/owslib-0.10.3-py35_0.tar.bz2\npandas                    0.17.1              np110py35_0    defaults\npatchelf                  0.8                           0    defaults\npath.py                   8.1.2                    py35_1    defaults\npatsy                     0.4.0               np110py35_0    defaults\npbr                       1.3.0                    py35_0    defaults\npep8                      1.6.2                    py35_0    defaults\npexpect                   3.3                      py35_0    defaults\npickleshare               0.5                      py35_0    defaults\npillow                    3.1.0                    py35_0    defaults\npip                       7.1.2                    py35_0    defaults\nplotly                    1.9.5                     <pip>\nply                       3.8                      py35_0    defaults\npostgresql                9.1.4                         0    defaults\nproj.4                    4.9.1                         1    https://conda.binstar.org/ioos/linux-64/proj.4-4.9.1-1.tar.bz2\nproj4                     4.9.1                         1    SciTools\npsutil                    3.3.0                    py35_0    defaults\nptyprocess                0.5                      py35_0    defaults\npy                        1.4.30                   py35_0    defaults\npyasn1                    0.1.9                    py35_0    defaults\npycosat                   0.6.1                    py35_0    defaults\npycparser                 2.14                     py35_0    defaults\npycrypto                  2.6.1                    py35_0    defaults\npycurl                    7.19.5.1                 py35_2    defaults\npyepsg                    0.2.0                    py35_0    SciTools\npyflakes                  1.0.0                    py35_0    defaults\npygments                  2.0.2                    py35_0    defaults\npyodbc                    3.0.10                   py35_0    defaults\npyopenssl                 0.15.1                   py35_1    defaults\npyparsing                 2.0.3                    py35_0    defaults\npyproj                    1.9.4                    py35_1    defaults\npyqt                      4.11.4                   py35_1    defaults\npyshp                     1.2.3                    py35_0    https://conda.binstar.org/ioos/linux-64/pyshp-1.2.3-py35_0.tar.bz2\npytables                  3.2.2               np110py35_0    defaults\npytest                    2.8.1                    py35_0    defaults\npython                    3.5.1                         0    defaults\npython-dateutil           2.4.2                    py35_0    defaults\npytz                      2015.7                   py35_0    defaults\npyyaml                    3.11                     py35_1    defaults\npyzmq                     15.2.0                   py35_0    defaults\nqt                        4.8.7                         1    defaults\nqtconsole                 4.1.1                    py35_0    defaults\nrasterio                  0.25.0              np110py35_0    defaults\nreadline                  6.2                           2    defaults\nredis                     2.6.9                         0    defaults\nredis-py                  2.10.3                   py35_0    defaults\nrequests                  2.9.1                    py35_0    defaults\nrope                      0.9.4                    py35_1    defaults\nrope-py3k-0.9.4           1                         <pip>\nscikit-image              0.11.3              np110py35_0    defaults\nscikit-learn              0.17               np110py35_p1  [mkl]  defaults\nscipy                     0.16.1             np110py35_p0  [mkl]  defaults\nseaborn                   0.6.0               np110py35_0    defaults\nsetuptools                19.2                     py35_0    defaults\nshapely                   1.5.11                   py35_0    defaults\nsimplegeneric             0.8.1                    py35_0    defaults\nsimplejson                3.8.1                     <pip>\nsip                       4.16.9                   py35_0    defaults\nsix                       1.10.0                   py35_0    defaults\nsnowballstemmer           1.2.0                    py35_0    defaults\nsnuggs                    1.3.1               np110py35_0    defaults\nsockjs-tornado            1.0.1                    py35_0    defaults\nsphinx                    1.3.1                    py35_0    defaults\nsphinx-rtd-theme          0.1.7                     <pip>\nsphinx_rtd_theme          0.1.7                    py35_0    defaults\nspyder                    2.3.8                    py35_0    defaults\nspyder-app                2.3.8                    py35_0    defaults\nsqlalchemy                1.0.11                   py35_0    defaults\nsqlite                    3.9.2                         0    defaults\nstatsmodels               0.6.1               np110py35_0    defaults\nsympy                     0.7.6.1                  py35_0    defaults\ntables                    3.2.2                     <pip>\nterminado                 0.5                      py35_1    defaults\ntheano                    0.7.0               np110py35_0    defaults\ntk                        8.5.18                        0    defaults\ntoolz                     0.7.4                    py35_0    defaults\ntornado                   4.3                      py35_0    defaults\ntraitlets                 4.1.0                    py35_0    defaults\nujson                     1.33                     py35_0    defaults\nunicodecsv                0.14.1                   py35_0    defaults\nunixodbc                  2.3.1                         1    defaults\nutil-linux                2.21                          0    defaults\nwerkzeug                  0.11.3                   py35_0    defaults\nwheel                     0.26.0                   py35_1    defaults\nxerces-c                  3.1.2                         0    defaults\nxlrd                      0.9.4                    py35_0    defaults\nxlsxwriter                0.8.2                    py35_0    defaults\nxlwt                      1.0.0                    py35_0    defaults\nxz                        5.0.5                         0    defaults\nyaml                      0.1.6                         0    defaults\nzeromq                    4.1.3                         0    defaults\nzlib                      1.2.8                         0    defaults\n"
 }
]
```

```{.python .input  n=8}
#List of installed pip packages
!pip list
```

```{.json .output n=8}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "abstract-rendering (0.5.1)\naccelerate (2.0.0)\naffine (1.2.0)\nalabaster (0.7.6)\nanaconda-client (1.2.1)\nargcomplete (1.0.0)\nastropy (1.1.1)\nBabel (2.1.1)\nbasemap (1.0.7)\nbeautifulsoup4 (4.4.1)\nbitarray (0.8.1)\nblaze (0.9.0)\nbokeh (0.11.0)\nboto (2.38.0)\nBottleneck (1.0.0)\ncffi (1.2.1)\nclick (4.1)\nclick-plugins (1.0.2)\ncligj (0.2.0)\nclyent (1.2.0)\ncolorama (0.3.3)\ncolorlover (0.2.1)\nconda (3.19.0)\nconda-build (1.18.2)\nconda-env (2.4.5)\nconfigobj (5.0.6)\ncryptography (0.9.3)\ncufflinks (0.7.1)\ncycler (0.9.0)\nCython (0.23.4)\ncytoolz (0.7.4)\ndatashape (0.5.0)\ndecorator (4.0.6)\ndescartes (1.0.1)\ndocutils (0.12)\ndynd (9b63882)\net-xmlfile (1.0.1)\nfastcache (1.0.2)\nFiona (1.6.0)\nFlask (0.10.1)\nfuncsigs (0.4)\nGDAL (2.0.0)\ngreenlet (0.4.9)\nh5py (2.5.0)\nhtml5lib (0.9999999)\nidna (2.0)\niopro (1.7.2)\nipykernel (4.2.2)\nipython (4.0.2)\nipython-genutils (0.1.0)\nipywidgets (4.1.1)\nitsdangerous (0.24)\njdcal (1.2)\njedi (0.9.0)\nJinja2 (2.8)\njsonschema (2.4.0)\njupyter (1.0.0)\njupyter-client (4.1.1)\njupyter-console (4.1.0)\njupyter-core (4.0.6)\nllvmlite (0.8.0)\nlxml (3.5.0)\nMarkupSafe (0.23)\nmatplotlib (1.5.1)\nmistune (0.7.1)\nmock (1.3.0)\nmultipledispatch (0.4.8)\nnbconvert (4.1.0)\nnbformat (4.0.1)\nnetworkx (1.10)\nnltk (3.1)\nnose (1.3.7)\nnotebook (4.1.0)\nnumba (0.22.1)\nnumbapro (0.22.1)\nnumexpr (2.4.4)\nnumpy (1.10.2)\nodo (0.4.0)\nopenpyxl (2.3.2)\nOWSLib (0.10.3)\npandas (0.17.1)\npath.py (0.0.0)\npatsy (0.4.0)\npbr (1.3.0)\npep8 (1.6.2)\npexpect (3.3)\npickleshare (0.5)\nPillow (3.1.0)\npip (8.0.2)\nplotly (1.9.5)\nply (3.8)\npsutil (3.3.0)\nptyprocess (0.5)\npy (1.4.30)\npyasn1 (0.1.9)\npycosat (0.6.1)\npycparser (2.14)\npycrypto (2.6.1)\npycurl (7.19.5.1)\npyepsg (0.2.0)\npyflakes (1.0.0)\nPygments (2.0.2)\npyodbc (3.0.10)\npyOpenSSL (0.15.1)\npyparsing (2.0.3)\npyproj (1.9.4)\npyshp (1.2.3)\npytest (2.8.1)\npython-dateutil (2.4.2)\npytz (2015.7)\nPyYAML (3.11)\npyzmq (15.2.0)\nqtconsole (4.1.1)\nrasterio (0.25.0)\nredis (2.10.3)\nrequests (2.9.1)\nrope-py3k (0.9.4.post1)\nscikit-image (0.11.3)\nscikit-learn (0.17)\nscipy (0.16.1)\nseaborn (0.6.0)\nsetuptools (19.2)\nShapely (1.5.11)\nsimplegeneric (0.8.1)\nsimplejson (3.8.1)\nsix (1.10.0)\nsnowballstemmer (1.2.0)\nsnuggs (1.3.1)\nsockjs-tornado (1.0.1)\nSphinx (1.3.1)\nsphinx-rtd-theme (0.1.7)\nspyder (2.3.8)\nSQLAlchemy (1.0.11)\nstatsmodels (0.6.1)\nsympy (0.7.6.1)\ntables (3.2.2)\nterminado (0.5)\nTheano (0.7.0)\ntoolz (0.7.4)\ntornado (4.3)\ntraitlets (4.1.0)\nujson (1.33)\nunicodecsv (0.14.1)\nWerkzeug (0.11.3)\nwheel (0.26.0)\nxlrd (0.9.4)\nXlsxWriter (0.8.2)\nxlwt (1.0.0)\n"
 }
]
```

## Running dynamic presentations

You need to install the [RISE Ipython
Library](https://github.com/damianavila/RISE) from [Damián
Avila](https://github.com/damianavila) for dynamic presentations

To convert and run this as a static presentation run the following command:

```{.python .input}
# Notes don't show in a python3 environment

!ipython nbconvert 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb --to slides --post serve


```

```{.json .output n=None}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "[TerminalIPythonApp] WARNING | Subcommand `ipython nbconvert` is deprecated and will be removed in future versions.\n[TerminalIPythonApp] WARNING | You likely want to use `jupyter nbconvert`... continue in 5 sec. Press Ctrl-C to quit now.\n[NbConvertApp] Converting notebook 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.ipynb to slides\n[NbConvertApp] Writing 327295 bytes to 20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.slides.html\n[NbConvertApp] Redirecting reveal.js requests to https://cdnjs.cloudflare.com/ajax/libs/reveal.js/3.1.0\nServing your slides at http://127.0.0.1:8000/20160202_Nottingham_GIServices_Lecture3_Beck_InteroperabilitySemanticsAndOpenData.slides.html\nUse Control-C to stop this server\nCreated new window in existing browser session.\nWARNING:tornado.access:404 GET /custom.css (127.0.0.1) 0.69ms\nWARNING:tornado.access:404 GET /favicon.ico (127.0.0.1) 0.86ms\n"
 }
]
```

To close this instances press *control 'c'* in the *ipython notebook* terminal
console

Static presentations allow the presenter to see *speakers notes* (use the 's'
key)

If running dynamically run the scripts below

## Pre load some useful libraries

```{.python .input  n=13}
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

```{.json .output n=13}
[
 {
  "name": "stdout",
  "output_type": "stream",
  "text": "Populating the interactive namespace from numpy and matplotlib\n"
 }
]
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



```{.python .input  n=1}
from IPython.display import YouTubeVideo
YouTubeVideo('xew6qI-6wNk')

```

```{.json .output n=1}
[
 {
  "data": {
   "image/jpeg": "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\n",
   "text/html": "\n        <iframe\n            width=\"400\"\n            height=\"300\"\n            src=\"https://www.youtube.com/embed/xew6qI-6wNk\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.YouTubeVideo at 0x7f31fc5ee490>"
  },
  "execution_count": 1,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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

```{.python .input  n=23}
from IPython.display import IFrame
IFrame('http://www.opengeospatial.org/standards', width=1000, height=700)
```

```{.json .output n=23}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://www.opengeospatial.org/standards\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f6ca5438c18>"
  },
  "execution_count": 23,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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

```{.python .input  n=21}
from IPython.display import IFrame
IFrame('http://www.osgeo.org/', width=1200, height=700)
```

```{.json .output n=21}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://www.osgeo.org/\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f6ca5438c50>"
  },
  "execution_count": 21,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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

```{.python .input}
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

```{.python .input}
from IPython.display import YouTubeVideo
YouTubeVideo('jUzGF401vLc')
```

\newpage

## Here's something I prepared earlier

A live presentation (for those who weren't at the event).....

```{.python .input  n=12}
from IPython.display import YouTubeVideo
YouTubeVideo('tkRB5Rp1_W4')

```

```{.json .output n=12}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"400\"\n            height=\"300\"\n            src=\"https://www.youtube.com/embed/tkRB5Rp1_W4\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.YouTubeVideo at 0x7f3ad00bc3d0>"
  },
  "execution_count": 12,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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


```{.python .input  n=14}
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/', width=1000, height=700)
```

```{.json .output n=14}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://lov.okfn.org/dataset/lov/\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005eb38>"
  },
  "execution_count": 14,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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

```{.python .input  n=19}
from IPython.display import IFrame
IFrame('http://www.opengeospatial.org/projects/groups/geosparqlswg', width=1000, height=700)
```

```{.json .output n=19}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://www.opengeospatial.org/projects/groups/geosparqlswg\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694008d780>"
  },
  "execution_count": 19,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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


```{.python .input  n=22}
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/doc/50kGazetteer/177276', width=1000, height=700)
```

```{.json .output n=22}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://data.ordnancesurvey.co.uk/doc/50kGazetteer/177276\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694008df60>"
  },
  "execution_count": 22,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=24}
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/id/postcodeunit/NG72QL', width=1000, height=700)
```

```{.json .output n=24}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://data.ordnancesurvey.co.uk/id/postcodeunit/NG72QL\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f69400ccac8>"
  },
  "execution_count": 24,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=20}
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/', width=1000, height=700)
```

```{.json .output n=20}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://data.ordnancesurvey.co.uk/\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694008dac8>"
  },
  "execution_count": 20,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=21}
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/ontology/', width=1000, height=700)
```

```{.json .output n=21}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://data.ordnancesurvey.co.uk/ontology/\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694008dc18>"
  },
  "execution_count": 21,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=17}
from IPython.display import IFrame
IFrame('http://data.ordnancesurvey.co.uk/datasets/code-point-open/explorer/sparql', width=1000, height=700)
```

```{.json .output n=17}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://data.ordnancesurvey.co.uk/datasets/code-point-open/explorer/sparql\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005e908>"
  },
  "execution_count": 17,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

## Open Street Map



```{.python .input  n=25}
from IPython.display import IFrame
IFrame('http://linkedgeodata.org/About', width=1000, height=700)
```

```{.json .output n=25}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://linkedgeodata.org/About\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f69400ccba8>"
  },
  "execution_count": 25,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=26}
from IPython.display import IFrame
IFrame('http://browser.linkedgeodata.org/', width=1000, height=700)


```

```{.json .output n=26}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://browser.linkedgeodata.org/\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005ebe0>"
  },
  "execution_count": 26,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

## Geonames


```{.python .input  n=27}
from IPython.display import IFrame
IFrame('http://www.geonames.org/ontology/documentation.html', width=1000, height=700)


```

```{.json .output n=27}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://www.geonames.org/ontology/documentation.html\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005e940>"
  },
  "execution_count": 27,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=28}
from IPython.display import IFrame
IFrame('http://www.geonames.org/maps/google_52.94_358.8.html', width=1000, height=700)


```

```{.json .output n=28}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://www.geonames.org/maps/google_52.94_358.8.html\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005e668>"
  },
  "execution_count": 28,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

```{.python .input  n=29}
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/vocabs/gn', width=1000, height=700)
```

```{.json .output n=29}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://lov.okfn.org/dataset/lov/vocabs/gn\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005ecc0>"
  },
  "execution_count": 29,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

\newpage

# Geo Vocabularies

```{.python .input  n=30}
from IPython.display import IFrame
IFrame('http://lov.okfn.org/dataset/lov/vocabs/?q=geo+space+address+geonames+os+spatial', width=1000, height=700)
```

```{.json .output n=30}
[
 {
  "data": {
   "text/html": "\n        <iframe\n            width=\"1000\"\n            height=\"700\"\n            src=\"http://lov.okfn.org/dataset/lov/vocabs/?q=geo+space+address+geonames+os+spatial\"\n            frameborder=\"0\"\n            allowfullscreen\n        ></iframe>\n        ",
   "text/plain": "<IPython.lib.display.IFrame at 0x7f694005e4e0>"
  },
  "execution_count": 30,
  "metadata": {},
  "output_type": "execute_result"
 }
]
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

```{.python .input}
and more

```

If X spatiallyContains Y and X is a city then Y is a place and Y is a cityPart.


Every city is a place.

What is a place.

```
```

```{.python .input}
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
