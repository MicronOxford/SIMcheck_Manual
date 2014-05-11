.. SIMcheck_Manual documentation master file, created by
   sphinx-quickstart on Sat May 10 23:03:53 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

SIMcheck Manual
===============

SIMcheck is a package of ImageJ tools for assessing the quality and reliability 
of Structured Illumination Microscopy (SIM) data. It should work with any
fairly recent ImageJ version, and can be installed by copying the
``SIMcheck_.jar`` file into your plugins folder and restarting ImageJ.
Although originally developed for API OMX data, SIMcheck may be used with data
from other systems including Zeiss's ELYRA and Nikon's N-SIM. It is implemented
as an ImageJ plugin bundle consisting of the main "SIMcheck" Dialog, which
assembles the required inputs and run multiple checks; and the individual
checks, which may also be run as stand-alone plugins. 

Contents:

.. toctree::
   :maxdepth: 2

   quickstart
   raw_data_checks
   SIR_data_checks
   cal_checks
   utils
   theory_gloss
   developer


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

