Raw Data Checks
===============

Channel Intensity Profiles (CIP)
--------------------------------

Average intensity is plotted for each slice (in the order: Phase, Z, Angle,
Time) where each channel is assigned an arbitrary color: 1st channel = red,
2nd = green, 3rd = blue, subsequent = black. This helps judge bleaching and whether all angles show
a similar intensity (as they should). An overall summary statistic is
reported for each channel: ``total intensity variation (%)``. This is for
a 9-Z window about the central Z-slice. The following additional statistics
each contribute to the total intensity variation, eenabling the source of
the problem to be identified:

* ``average intensity decay per 9 section window (%)``, due to photobleaching 
* ``maximum intensity difference between angles (%)``
* ``relative intensity fluctuations (%)``, due to illumination flicker

Motion & Illumination Variation (MIV)
-------------------------------------

This check highlights features that change in-between recording data for
different angles. Each angle (assumes 3!) is assigned a color: Cyan, Magenta,
or Yellow, meaning that if a feature is present in all angles it will appear
C+M+Y=White, or will exhibit the color of a specific angle(s) if not (the
color scheme chosen here is intended to make the distinction between angles
and channels clear). The reconstruction algorithm assumes that all features
are sampled at each angle, and features that move or experience different
illumination intensity for different angles (or phases) will result in
artifacts.

Fourier Projections (FPJ)
-------------------------

``This check is not turned on by default in the main dialog, since it it
requires a sample that fills a large porportion of the field of view and is
mainly intended for diagnosis of hardware issues.`` 2D Fourier Transforms of
the raw data are taken, and projected over all phases and angles. There are
sliders for channel and time where present.  When features are in-focus and
their intensities are modulated by the illumination pattern, 2D FFTs of each
plane in the raw SI data should show 1st and 2nd order spots along a line
perpendicular to the angle of illumination pattern stripes. Blurred, missing or
extra spots may indicate problems with the illumination pattern (although
sparse samples may lack clear spots in the FFT). Note that images with XY sizes
that are not a power of 2 (256x256, 512x512 and so on are power of 2) require
padding, which may lead to inferior results.

Modulation Contrast (MCN)
-------------------------

The ``Modulation Contrast-to-Noise Ratio`` (MCNR) is a ratio of SI illumination
pattern strength to noise strength - values less than 3 are inadequate
(purple), values ~6 are adequate (red), values of ~12 are good (orange), values
of ~18 are very good (yellow) and values of ~24 or better are excellent
(white). NB. the display range must not be changed from 0 to 24 for meaningful
interpretation of the Look-Up Table. The check reports an average MCNR value for
auto-thresholded image features (Otsu method), and an estimate for the optimal
``Wiener filter parameter`` for OMX data reconstruction based on this.

If the illumination pattern at a given feature is overpowered by the noise,
reconstruction will fail - any super-resolution features observed in such
regions cannot be trusted.
