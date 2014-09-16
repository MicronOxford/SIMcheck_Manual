Reconstructed Data Checks
=========================

Reconstructed Intensity Histogram (RIH)
---------------------------------

Overlays linear and logarithmic histograms showing relative contribution of
negative values to the SI-Reconstructed result for each channel. Ratio of
positive to negative values reported. Negative values indicatate
reconstruction artifacts. Where the ratio of positive to negative values at
the histogram extremes is less than 5-10, this indicates a poor
reconstruction.

Fourier plots (FTL, FTR, FTO)
-------------

Plots a 2D Fourier transform "target" plots showing resolution lines and
color-coded with a LUT to make relative proportion of different frequencies
more obvious. These plots help judge the average resolution in the sample
volume, limited by noise. A gradual decay of frequencies from the center
(lowest frequency) to the edge (highest frequency and resolution) indicates
real high resolution information; whereas a flat spectrum indicates only noise
at the higher frequencies. Reconstruction artifacts may also be apparent as
spots in the spectrum. Note that this check has the caveat that it is an
average for the volume, so if the ROI includes more background than signals of
interest it will be less meaningful.

Modulation Contrast Map (MCM)
-----------------------

This produces an RGB image displaying a combination of intensity information
and modulation contrast calculated from the raw data. Values 0-255 correspond
to 0-Stack Max, and Modulation contrast (<3 purple, to 6 red, to 12 orange, to
18 yellow, to 24 white). Features that are red-orange, yellow or white (i.e.
MCNR >6) can be considered reliable. Note that ImageJ shows the R,G,B pixel
values in its status bar when you hover over a pixel with the pointer. It is 
intended as a quantitative tool for assessing whether individual features in
the reconstructed data are supported by the raw data.
