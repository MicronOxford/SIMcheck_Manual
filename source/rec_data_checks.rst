Reconstructed Data Checks
=========================

Reconstructed Intensity Histogram (RIH)
---------------------------------

Overlays linear- and logarithmic-scaled intensity histograms (black and gray,
respectively) showing relative contribution of "negative" values to the
reconstructed result for each channel. Negative values are those below the
modal intensity value for background regions, and are due to reconstructed
noise and ringing artefacts at the edge of high-intensity features.
The ratio of positive to negative values at the histogram extrema is reported:
i.e. only a small percentage of the highest and lowest intensities (this
increases the robustness of the statistic to differences in the proprtion of
background versus features in the image). Where the ratio is less than 5-10,
this generally indicates a poor reconstruction.

Fourier plots (FTL, FTR, FTO)
-------------

Displays 2D Fourier transform "target" plots with resolution lines (in Microns)
and optionally blurred and color-coded with a 16-color Look-Up Table to make
the relative proportion of different frequencies more obvious. The plots
displayed are: "Fourier Transform Lateral (FTL)" for XY sections; "Fourier
Transform Radial (FTR)" which is a radial (circularly-averaged) profile though
the XY Fourier Trasform; and "Fourier Transform Orthogonal (FTO)" for the
central resliced XZ section.  These plots help judge the average resolution in
the sample volume, limited by noise. A gradual decay of frequencies from the
center (lowest frequency) to the edge (highest frequency and resolution)
indicates real high resolution information; whereas a flat spectrum indicates
only noise at the higher frequencies. The lateral (FTL) and radial (FTR) plots
give an indication on XY resolution, while the orthogonal (FTO) plot reports on
Z resolution as well.  Reconstruction artifacts may also be apparent as spots
in the Fourier spectrum, which are observed as regular, repeating patterns in
the image. Note that this check has the caveat that it is an average for the
volume, so if the image consists of more background than features of interest
it will be less meaningful.

When run stand-alone, there are a number of options to configure. The noise
cut-off may be manually specified for each channel instead of using the
"Threshold and 16-bit Conversion" utility; the gaussian window function used to
avoid Fourier Transform edge artefacts may be turned off; auto-scaling of the
Fourier Transform result from mode to maximum may be turned off; and the blur /
false-color look-up table option may be turned on.

Modulation Contrast Map (MCM)
-----------------------

This plugin produces an RGB image displaying a combination of intensity
information and modulation contrast calculated from the raw data: i.e. the
proportion of red, green and blue is adjusted to reflect modulation contrast
(<3 purple, to 6 red, to 12 orange, to 18 yellow, to 24 white), and the overall
intensity of each pixel is scaled according to intensity in the reconstructed
image. Features that are red-orange, yellow or white (i.e.  MCNR >6) can be
considered reliable. Additionally, pixels that are saturated in the raw data
are colored green in this map. Note that ImageJ shows the R,G,B pixel values in
its status bar when you hover over a pixel with the pointer. It is intended as
a quantitative tool for assessing whether individual features in the
reconstructed data are supported by the raw data.
