Utilities
=========

Format Converter
----------------

Converts non-API OMX format SIM data into the OMX's "CPZAT" dimension ordering,
since all of the Check plugins assume and require this dimension ordering to
work correctly. See :ref:`si-systems` for a discussion of the different
formats.

Raw SI Data to Pseudo-Widefield
-------------------------------

Generates a wide-field image by averaging all phases and angles, with the
option to normalise slice intensities using the same simple ratio strategy as
Fiji's ``Bleach Correction`` plugin.  The result is scaled to double the number
of pixels in X and Y, so that it matches typical reconstructed image
dimensions.  This enables comparison of wide-field and reconstructed SI images,
and checkng for the presence of features observed in the latter in the former.

Threshold and 16-bit Conversion
-------------------------------

Discards intensities below a threshold (automatic, or manually-defined per
channel) and converts the remainder to 16-bit data, filling the 16-bit range.
The automatic thresholding method uses the modal intensity value for each
channel in the stack. The effect should be equivalent to "discarding the
negative values".

Modulation Contrast Filter
--------------------------

The Modulation Contrast (MC) Filter reduces high-frequency noise
artifacts (``hammer finish``) from low modulation/stripe contrast in
the raw data. This is typically caused by low specific signal and/or
increased level of background, e.g. from out-of-focus blur. The
process masks all pixels in the reconstructed dataset where the
corresponding MCNR values in the raw data MCN map fall below an
empirically chosen threshold (default setting 4.0; use a higher
threshold value if the raw data quality is good and a lower threshold
if the raw data quality is bad). Prior thresholding the MCN map is
smoothened with a 2D Gaussian filter (default pixel radius 1.0). After
masking, the reconstructed dataset is blurred with a 3D Gaussian
filter (default pixel radius 1.0 in xy and z) to smoothen hard edges.

Stack FFT (2D)
--------------

Applies a 2D Fast Fourier Transform with Gaussian window function to each slice
in a stack. Three result types / scaling options are available: 1) log-scaled
amplitude squared, rescaled to 8-bit (i.e. ImageJ's default); 2) log-scaled
amplitude squared as 32-bit float; 3) gamma-scaled amplitude.
