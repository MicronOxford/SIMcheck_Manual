Raw Data Checks
===============

Angle Difference
----------------

This check shows features that move/float in-between recording data for
different angles. Each angle (assumes 3!) is assigned a color: Cyan, Magenta,
or Yellow, meaning that if a feature is present in all angles it will appear
C+M+Y=White, or will exhibit the color of a specific angle(s) if not (the
color scheme chosen here is intended to make the distinction between angles
and channels clear). The reconstruction algorithm assumes that all features
are sampled at each angle, and features that move or experience different
illumination intensity for different phases or angles will result in
artifacts.

Intensity Profiles
------------------

Average intensity is plotted for each plane (in the order: phase, Z, angle,
time) where each channel is assigned an arbitrary color: 1st channel = blue,
2nd = green, 3rd = red. This helps judge bleaching and whether all angles show
a similar intensity (as they should).

Fourier Plots
-------------

2D Fourier Transforms of each image slice are displayed, split into separate
hyperstacks according to angle. NB. results contain a "Z" dimension that is
actually phase then Z; there are sliders for channels and time. Where
features are in focus and their intensities are modulated by the
illumination pattern, 2D FFTs of each plane in the raw SI data should show
1st and hopefully 2nd order spots along a line perpendicular to the angle
of illumination pattern stripes.

Modulation Contrast
-------------------

The Modulation Contrast-to-Noise Ratio (MCNR) is a ratio of SI illumination
pattern strength to noise strength - values less than 3 are inadequate
(purple), values ~6 are adequate (red), values of ~12 are good (orange),
values of ~18 are very good (yellow) and values of ~24 or better are excellent
(white). NB. the display range must not be changed from 0 to 24 for meaningful
interpretation of the Look-Up Table. Also reports an average MCNR value for
auto- thresholded image features (triangle method), and an estimate for the
optimal Wiener filter parameter for OMX data reconstruction.

If the illumination pattern at a given feature is overpowered by the noise,
reconstruction will fail - any features observed in such regions cannot be
trusted.

The actual calculation carried out is, for each voxel in the real 3D image:

#. A variance stabilizing Anscombe transform is performed out so that noise follows
   an approximately Gaussian rather than Poissonian distribution.

#. All phases are lined up (in fact, a "Z window" of such phase series is
   assembled - e.g. for Z window = 1, 2Z+1=3 Z planes are considered, so for Z
   window = 1 and 5 phases we have 15 planes - this is to increase
   signal-to-noise to a similar extent to the "band filtering" performed during
   reconstruction) and Fourier transformed to create a power spectrum of the
   various frequencies present.  

#. The power of the frequency components corresponding to the illumination
   pattern modulation are divided by the average of the highest frequency
   component for the same Z plane (taken to be dominated by noise). The position
   of the modulation frequency component is given by: 
     ``vector_length * order / phases``

#. values of "MCNR" that are consistent with satisfactory versus
   unsatisfactory reconstructions were determined empirically, but are in
   reasonable agreement with the "Rose criterion" which states that a
   contrast-to-noise ratio of more than 5 is required for reliable detection of
   a signal.
