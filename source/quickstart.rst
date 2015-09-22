.. _quick-start:

Quick Start
===========

SIMcheck is implemented as an ImageJ plugin bundle consisting of the main 
"SIMcheck" Dialog, which assembles the required inputs and runs multiple 
checks; and the individual checks, which may also be run as stand-alone plugins.

To get started, after installing the Plugin, you need to open **two
datasets**: the **raw data** file, and the corresponding **reconstructed
data** file. Before running SIMcheck, import the data as a single stack.
NB. SIMcheck can be used to convert ELYRA and N-SIM data to the OMX
dimenson ordering via the main SIMcheck plugin or the menu option
``SIMcheck > Utilities > Format Converter``.

.. _fig1a:

    .. image:: images/SIMcheckStart.jpg
        :width: 480px
        :align: center
        :alt: SIMcheck main dialog

    **Figure 1a.** SIMcheck main dialog, with raw and reconstructed data.

Before running the checks **it is best to crop to a region containing the
features of interest**, but including a representative area of background
features. Preferably crop in XY to a square region of size 256x256 or 512x512
(i.e. a power of 2). The main SIMcheck dialog allows cropping parameters to be
specified using reconstructed data slice numbers and Region-Of-Interest.
Cropping improves Fourier- and histogram-based checks, which reflect average
properties for the field of view, and also saves time and reduces the chance of
running out of memory (NB. memory allocated to ImageJ can be adjusted in ``Edit
> Options > Memory & threads``). 

Specify image stacks to use, checks to run, and ensure additional parameters
(i.e. Phases, Angles, Camera Bit-Depth) are correct. The "Modulation Contrast
Map" requires both raw and reconstructed images to be selected - alternatively,
when run standalone you can specify a previously-calculated MCNR image.
**Make sure your reconstruction shows negative values** - do not
discard them (if you must) until later. Click on the OK button to start
running the checks. Next choose "Run SIMcheck" from the "SIMcheck" submenu
in your Plugins menu. Output images will be displayed, and statistics and
information will appear in the ImageJ log window. Finally, a Results window
containing a summary of the key numerical statistics is displayed.

.. _fig1b:

    .. image:: images/SIMcheckChecks.jpg
       :width: 60 %
       :alt: SIMcheck output images
    .. image:: images/SIMcheckLogs.png
       :width: 38 %
       :alt: SIMcheck log and summary

    **Figure 1b.** SIMcheck output: check output images, log and summary.

SIMcheck is able to handle handle multi-channel data and time
series, but for large datasets you may find it best to split channels
and analyze them separately if memory is an issue (running all checks
requires additional memory equal to approximately 4x that taken up by
the raw + reconstructed data). 

Each check can alternatively be run alone by selecting from the other
menu items, and some checks contain additional options when run in this way.
There are also tools to convert raw SI data to pseudo-widefield, and
"calibration" tools, intended to diagnose SIM microscope setup issues.
