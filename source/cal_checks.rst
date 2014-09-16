System Calibration
==================

Illumination Pattern Focus (IPF)
--------------------------------

This plugin takes raw SIM data (1 Channel, 1 Time-point) for a bead lawn, and
shows an axial side-view of the illumination pattern for the first phase of
each angle. This is obtained by rotating the illumination pattern for each
angle so that it is vertically-aligned, reslicing the central half of the
rotated image, and performing a maximum intensity projection along the
direction of the stripes. The separate angles are displayed stacked as a
montage. Ideally, each bead should have the appearance of a point-spread
function. A zipper-like pattern, on the other hand, is indicative of a poorly
focussed illumination pattern or incorrect phase settings where the
illumination pattern is created by interference of multiple beams.

Illumination Phase Steps (IPS)
------------------------------

This plugin checks system stability and alignment by detecting illumination
pattern frequencies and plotting the phase steps. The SIM illumination pattern
should be in-focus and the sample should fill most of the field of view: a bead
lawn or fluorescent ink slide works well. In addition to plotting the phase
steps for visual inspection, a number of statistics are also reported: these
are the standard deviations of the illumination pattern frequency, the phase
step size, and reproducibility of the offset (i.e. whether the phase returns to
the same position after each cycle or not). **Note: this plugin is a work in
progress, and the phase unwrapping and statistics are not yet reliable.**

Spherical Aberration Mismatch (SAM)
-----------------------------------

This check plots the minimum and the mean value in each slice, and summarizes
the standard deviation of the minimum value normalized by the stack mode
intensity. Large variations in the minimum value relative to the average
indicate mismatch between the spherical aberration present when the sample
and point spread function data were acquired.
