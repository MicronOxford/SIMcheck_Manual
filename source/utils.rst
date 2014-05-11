Utilities
=========

FFT Stack (2D)
--------------

Applies a 2D FFT with Gaussian window function to each slice in a stack.

Raw Data to Pseudo-Widefield
----------------------------

Generates a wide-field image by averaging phases (and optionally all angles),
This enables comparison of wide-field and reconstructed SI images, and checkng
for the presence of features observed in the latter in the former.

SIM Format Converter
--------------------

Converts non-API OMX format SIM data into the OMX's "CPZAT" dimension
ordering, since all of the Check plugins assume and require this dimension
ordering to work correctly.
