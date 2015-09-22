Reconstructed Data Checks
=========================

Reconstructed Intensity Histogram (RIH)
---------------------------------------

Displays an overlay of linearly- and logarithmically-scaled intensity
histograms (black and gray, respectively) showing relative contribution of
"negative" values to the reconstructed result for each channel. Negative values
are those below the average (mode) intensity value for background regions, and
are due to reconstructed noise and ringing artefacts at the edge of
high-intensity features. The **Max-to-Min intensity Ratio** (MMR; positive
versus negative intensities at the histogram extrema) is reported: i.e. only a
small percentage of the highest and lowest intensities (this increases the
robustness of the statistic to differences in the proprtion of background
versus features in the image). A ratio less than 3 generally indicates poor
reconstruction; a ratio above 6 indicates good reconstruction.

N.B. **This check requires a non-thresholded reconstructed dataset**: any
option that discards low intensities, such as "discard negatives" in GE's
SoftWoRx software, should be disabled.

.. _fig3a:

    .. image:: images/Checks_Rec/Rec_RIH_good.jpg
        :width: 300px
        :alt: RIH histogram and image for good reconstruction
    .. image:: images/Checks_Rec/Rec_RIH_poor.jpg
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
e.g. a bead lawn, to work reliably.* 

The SAM check plots the minimum and the mean value in
each slice, and summarizes the standard deviation of the minimum value
normalized by the stack mode intensity, the **Z Minimum Variation** (ZMV).
Large variations in the minimum value relative to the average indicate mismatch
between the spherical aberration present when the sample and point spread
function data were acquired.

.. _fig3b:

    .. image:: images/Checks_Rec/Rec_SAM_good.jpg
        :width: 300px
        :alt: SAM plot and image without mismatch
    .. image:: images/Checks_Rec/Rec_SAM_poor.jpg
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

**Note that this check evaluates the image volume's average characteristics. It
is therefore recommended to select an image region with a high proportion of
features as well as some background. A very high proportion of background can
make it difficult to discern the contribution from the features of interest.**

Displays 2D Fourier transform "target" plots with overlaid resolution lines (in Microns)
and optionally blurred and color-coded with a 16-color look-up table to make
the relative proportion of different frequencies more obvious. The plots
displayed are: Fourier Transform Lateral (FTL) for XY sections; Fourier
Transform Radial (FTR) which is a radial (circularly-averaged) profile though
the XY Fourier Trasform; and optionally, Fourier Transform Orthogonal (FTO) for the
central resliced XZ section (N.B. ensure the central Y point contains some
features of interest). These plots help judge the average resolution in
the sample volume, limited by noise. A gradual decay of frequencies from the
center (lowest frequency) to the edge (highest frequency and resolution)
indicates real high resolution information; whereas a flat spectrum indicates
predominantly noise at the higher frequencies. The lateral (FTL) and radial (FTR) plots
give an indication on XY resolution, while the axial (FTO) plot reports on
Z resolution as well.

.. _fig3c:

    .. image:: images/Checks_Rec/Rec_FTL_good.png
        :width: 220px
        :alt: FTL plot for a high resolution image
    .. image:: images/Checks_Rec/Rec_FTL_lowres.png
        :width: 220px
        :alt: FTL plot for a low resolution image
    .. image:: images/Checks_Rec/Rec_FTO_good.png
        :width: 220px
        :alt: FTO plot for the high resolution image
    .. image:: images/Checks_Rec/Rec_FTR_good.png
        :width: 225px
        :alt: FTR plot for a high resolution image
    .. image:: images/Checks_Rec/Rec_FTR_lowres.png
        :width: 225px
        :alt: FTR plot for a low resolution image

    **Figure 3c.** The top row shows 2D Fourier transform amplitudes (log-
    scaled). Top left: a high resolution dataset; middle: a noisy, low 
    resolution dataset showing a "hard edge" (red arrow) and obvious
    "flower pattern"; right: 2D Fourier transform of an orthogonally
    resliced (i.e. axial) cross-section through the image, which reports
    on Z resolution. Bottom: radial profile plots derived from the lateral
    Fourier transform images in the top row. In the FTR plot for the left-hand
    high resolution image, frequency amplitudes decay smoothly until 1/8 to
    1/10 microns, i.e. a resolution of ~120 nm. In the poorer middle dataset,
    frequency amplitudes decay rapidly, disappearing into the noise by
    ~200 nm. The second, rapid drop at 125-100 nm corresponds to the
    frequency support limit of the OTF.

Reconstruction artifacts may also be apparent as spots in the Fourier spectrum,
which are observed as regular, repeating patterns in the image. 

.. _fig3d:

    .. image:: images/Checks_Rec/Rec_FTL_artifact.jpg
        :width: 500px
        :align: center
        :alt: FTL plot showing spots (artifacts)

    **Figure 3d.** An image containing reconstruction artifacts shown top left,
    with a blow-up of top right of the image shown bottom right. Spots are 
    evident in the 2D Fourier transform "FTL" plot, highlighted with a red
    arrow. In the reconstructed image these reconstuction artifacts can be seen
    as repeating hexagonal patterns.

When run as a stand-alone plugin, there are a number of options to configure.
The default display option is to apply a cut-off at the modal intensity value
before Fourier transformation, which is equivalent to "Discard Negatives"
in the OMX reconstruction software or "Baseline Cut / Shifted" in the ELYRA
reconstruction software. Default is to display the FFT amplitude, gamma-scaled
(gamma=0.2). Other options are:

* **Cut-off: manual**, which is equivalent to thresholding the image at the
  intensity value(s) chosen (i.e. if thresholding at an intensity value other
  than the modal intensity is necessary).

* **Window function**, which reduces spurious high frequencies in the FFT of
  images with features that reach to the edges of the image.

* **32-bit Amp, gamma 0.2, display min-max**, which is the same as the
  default option, but with a final display scaling step based on image content.

* **8-bit log(Amp^2), display mode-max**, which is similar to ImageJ's 
  default FFT "power spectrum" display, and 1) emphasies high frequencies;
  2) produces a result that takes up less memory (i.e. may be useful for
  large datasets).

* **Blur & false-color LUT** (described above, off by default)

* **Show axial FFT** (described above, off by default)

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

.. _fig3e:

    .. image:: images/Checks_Rec/Rec_MCM_MTs.png
        :width: 450px
        :align: center
        :alt: MCM map highlighting high and low resolution microtubules.

    **Figure 3e.** Modulation Contrast Map for a MicroTubule (MT) sample. Note
    the Look-Up Table at the bottom right of the image shows the corresponding
    modulation contrast value for each color. A MT filament with low modulation
    contrast (0-6, purple-red) is highlighted with a red arrow: this implies
    lower resolution / less reliable high resolution features than microtubles
    with a modulation contrast >6 (orange/yellow/white).
