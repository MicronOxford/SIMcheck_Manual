Quick Start
===========

SIMcheck is implemented as an ImageJ plugin bundle consisting of the main 
"SIMcheck" Dialog, which assembles the required inputs and run multiple 
checks; and the individual checks, which may also be run as stand-alone plugins.

To get started, after installing the Plugin, you need to open **two
datasets**: the **raw SI data** file, and the corresponding **reconstructed
"SIR" data** file. Before running SIMcheck, import the data as a single stack.
NB. SIMcheck can be used to convert ELYRA and N-SIM data to the API OMX 
dimenson ordering via the main SIMcheck plugin or the menu option
SIMcheck->Utilities->SIM format converter. 

**It is best to crop to a region containing the features of interest**
before running the checks (draw a ROI and then Image->Duplicate). This
improves Fourier- and histogram-based checks, which reflect average
properties for the field of view, and also saves time and reduces the
chance of running out of memory (NB. memory allocated to ImageJ can be
adjusted in Edit->Options->Memory & threads). 

Specify image stacks to use, checks to run, and provide/check the
additional parameters (i.e. Phases and Angles). The "SIR Mod Contrast Map"
requires both raw SI and SIR reconstructed images to be selected -
alternatively, when run standalone you can specify a previously-calculated
MCNR image. **Make sure your reconstruction shows negative values** - do not
discard them (if you must) until later. Click on the OK button to start
running the checks. Next choose "Run SIMcheck" from the "SIMcheck" submenu
in your Plugins menu. Output images will be displayed, and statistics and
information will appear in the ImageJ log window.

SIMcheck should be able to handle handle multi-channel data and time
series, but for large datasets you may find it best to split channels
and analyze them separately if memory is an issue (running all checks
requires additional memory equal to approximately 4x that taken up by
the raw + processed data). 

Each check can alternatively be run alone by selecting from the other
menu options, where there are also tools to convert raw SI data to
pseudo-widefield, and "calibration" tools, intended to diagnose 
SIM microscope setup issues.
