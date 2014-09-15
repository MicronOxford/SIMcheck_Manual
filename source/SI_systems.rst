SI Microscopy Systems
=====================

OMX
---

The OMX systems from GE Healthcare (formerly API) are based on a prototype built in the lab of John Sedat at UCSF. All versions share a common file format: this is an MRC file format adapted for the DeltaVision family of wide-field deconvolution microscopes (also originating at UCSF in the Sedat and Agard labs), as described in the online documentation of their Priism image processing package.

Data are acquired in several different schemes by the different versions of OMX microscope, but all are stored in a "CPZAT" dimension order: i.e. channel, then phase, then Z-plane, then angle, then time frame. When opening such data in ImageJ, one usually sees all phases and angles subsumed into the Z dimension, meaning Zobserved=P*Zreal*A, with phase varying fasest, then real Z, and finally the angle. Note that bleaching, dependent on the true order of data acquisition, may well be apparent when using the "Channel Intensity Profiles" check. OMX microscopes invariably acquire 3 angles and 5 phases of the illumination pattern.

Zeiss ELYRA
-----------

The Zeiss ELYRA system has greater flexibility in terms of the number of different angles acquired, with both 3 angles and 5 angles typically used (the latter produces higher quality reconstructions given a sufficiently photostable sample). The number of phases is limited to 5 as for the API OMX systems.

ELYRA data are typically stored in .czi format files, with different angles and phases stored as separate series within a single file. Note that the LOCI Bio-Formats importer (which Fiji ImageJ uses by default) is able to concatenate the separate series upon import if the "Concatenate series when compatible" box is ticked (in the "Dataset organization" section of the Import Options Dialog), which is recommended for use with SIMcheck. See the figure below.

In this case, the resulting hyperstack will have the phases and angles subsumed into the time dimension, with the real time varying fastest, then angle, then finally phase: i.e. T_observed = T_real*angle*phase. SIMcheck re-orders the data into the OMX "CPZAT" order prior to running the pre-processing checks for convenience.

Nikon N-SIM
-----------

Nikon N-SIM raw data are stored as tiled images in .nd2 files; where phases are tiled in the x-direction, angles in the y-direction.
