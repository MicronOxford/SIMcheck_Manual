Quick Start
===========

SIMcheck is implemented as an ImageJ plugin bundle consisting of the main 
"SIMcheck" Dialog, which assembles the required inputs and run multiple 
checks; and the individual checks, which may also be run as stand-alone plugins.

To get started, after installing the Plugin, you need to open two
datasets: the raw SI data file, and the corresponding reconstructed
SIR file. Next choose "Run SIMcheck" from the new "SIMcheck" submenu
in your Plugins menu. The "help" button provides a link to the current
online manual, which provides explanations of the different tests.
Output images will be displayed, and statistics and information will
appear in the ImageJ log window.

SIMcheck should be able to handle handle multi-channel data and time
series, but for large datasets you may find it best to split channels
and analyze them separately if memory is an issue (running all checks
requires additional memory equal to approximately 4x that taken up by
the raw + processed data). Cropping the data to a region containing 
the cells / features of interest is also a good idea for Fourier- and
histogram-based checks, which reflect average properties for the
field of view.

Each check is a separate plugin, and can alternatively be run alone
by selecting from the other menu options. There are also tools to
convert from non-OMX data formats (ELYRA, NSIM), convert raw SI data
to pseudo-widefield, and unfinished "calibration" tools, intended to
diagnose SIM microscope setup issues.
