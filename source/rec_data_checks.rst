Reconstructed Data Checks
=========================

Reconstructed Intensity Histogram (RIH)
---------------------------------------

Overlays linear- and logarithmic-scaled intensity histograms (black and gray,
respectively) showing relative contribution of "negative" values to the
reconstructed result for each channel. Negative values are those below the
modal intensity value for background regions, and are due to reconstructed
noise and ringing artefacts at the edge of high-intensity features.  The
**Max-to-Min intensity Ratio** (MMR; positive versus negative intensities at
the histogram extrema) is reported: i.e. only a small percentage of the highest
and lowest intensities (this increases the robustness of the statistic to
differences in the proprtion of background versus features in the image). Where
the ratio is less than 5-10, this generally indicates a poor reconstruction.

.. _fig3a:

    .. image:: http://localhost/~gball/SIMcheck_Examples/Checks_Rec/Rec_RIH_good.jpg
        :width: 300px
        :alt: RIH histogram and image for good reconstruction
    .. image:: http://localhost/~gball/SIMcheck_Examples/Checks_Rec/Rec_RIH_poor.jpg
        :width: 300px
        :alt: RIH histogram and image for poor reconstruction

    **Figure 3a.** Reconstructed images and intensity histograms for a good
    (left) and poor (right) reconstruction. The histogram peak corresponds
    to the centre of the background intensity distribution, i.e. reconstructed
    noise. Ideally this peak should be narrow. Intensity information for real
    features should extend in the positive direction only, which it clearly
    does to a greater extent in the histogram on the left.

Spherical Aberration Mismatch (SAM)
-----------------------------------

*This check is not enabled by default, as it requires an appropriate sample,
e.g. a bead lawn, to work reliably.* It plots the minimum and the mean value in
each slice, and summarizes the standard deviation of the minimum value
normalized by the stack mode intensity, the **Z Minimum Variation** (ZMV).
Large variations in the minimum value relative to the average indicate mismatch
between the spherical aberration present when the sample and point spread
function data were acquired.

.. _fig3b:

    .. image:: http://localhost/~gball/SIMcheck_Examples/Checks_Rec/Rec_SAM_good.jpg
        :width: 300px
        :alt: SAM plot and image without mismatch
    .. image:: http://localhost/~gball/SIMcheck_Examples/Checks_Rec/Rec_SAM_poor.jpg
        :width: 300px
        :alt: SAM plot and image with mismatch

    **Figure 3b.** Reconstructed images and slice mean/min plots for a
    reconstruction without (left) and with (right) spherical aberration mismatch.
    A characteristic dip in the minimum value indicating mismatch is shown with
    a red arrow in the bottom right plot. This corresponds to the dark
    (negative) fringe around the edge of the nucleus, also marked with a red
    arrow in the image data top right.

Fourier plots (FTL, FTR, FTO)
-----------------------------

Displays 2D Fourier transform "target" plots with resolution lines (in Microns)
and optionally blurred and color-coded with a 16-color Look-Up Table to make
the relative proportion of different frequencies more obvious. The plots
displayed are: "Fourier Transform Lateral (FTL)" for XY sections; "Fourier
Transform Radial (FTR)" which is a radial (circularly-averaged) profile though
the XY Fourier Trasform; and "Fourier Transform Orthogonal (FTO)" for the
central resliced XZ section (N.B. ensure the central Y point contains some
features of interest). These plots help judge the average resolution in
the sample volume, limited by noise. A gradual decay of frequencies from the
center (lowest frequency) to the edge (highest frequency and resolution)
indicates real high resolution information; whereas a flat spectrum indicates
only noise at the higher frequencies. The lateral (FTL) and radial (FTR) plots
give an indication on XY resolution, while the orthogonal (FTO) plot reports on
Z resolution as well. Reconstruction artifacts may also be apparent as spots
in the Fourier spectrum, which are observed as regular, repeating patterns in
the image. Note that this check has the caveat that it is an average for the
volume, so if the image consists of more background than features of interest
it will be less meaningful.

When run stand-alone, there are a number of options to configure. The noise
cut-off may be manually specified for each channel instead of using the
"Threshold and 16-bit Conversion" utility; you may choose not to use a noise
cut-off at all; the gaussian window function used to avoid Fourier Transform
edge artefacts may be turned off; auto-scaling of the Fourier Transform result
from mode to maximum may be turned off; and the blur / false-color look-up
table option may be turned on.

Modulation Contrast Map (MCM)
-----------------------------

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
