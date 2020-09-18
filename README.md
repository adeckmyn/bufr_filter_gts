# bufr_filter_gts (BFG)
A python3 toolbox for filtering GTS messages in BUFR format

This toolbox implements a simple python3 module for filtering BUFR-synop messages from GTS into single BUFR files, taking into account all duplications, corrections etc. It is based on the python module *eccodes*.

Alex Deckmyn, 2020
Royal Meteorological Institute
alex.deckmyn@meteo.be

This software is distributed under the Apache license (>=2.0)

This repository contains
1. a python3 module bufr_filter_gts which should made available to python
   - PYTHONPATH=<.../bufr_filter_gts/module>
   - or copy the bufr_toolbox module to python library path
2. a sample script that calls this module to make a BUFR extraction
3. some outdated documentation

CONFIGURATION:
--------------

You will probably have to modify a few routines in /synop_extractor.py/, depending how incoming GTS data is stored.
- **update_sqlite()** :
in this function, you may need to adapt the directory structure for GTS input. 
At RMI, it is organised in hourly directories "YYYYMMDDHH"
(this is the time that the GTS message arrives and may be quite different from the date to which it refers internally!)
Just look for the *newdir* and *gtsdir* lines.
- Default is to create HOURLY BUFR FILES ([time - 29', time+30'])
You can modify the window size *obs_window_size=60* in the main call to *update_sqlite()*. 
But to change the centering, you will have to modify the function **obs_window()**.

