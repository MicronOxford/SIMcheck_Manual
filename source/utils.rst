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

Stack FFT (2D)
--------------

Applies a 2D Fast Fourier Transform with Gaussian window function to each slice
in a stack.
