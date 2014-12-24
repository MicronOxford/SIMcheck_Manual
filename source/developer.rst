Developer Documentation
=======================

The SIMcheck project uses Apache Maven [#]_ as a build and dependency
management tool. After the ``mvn package`` phase, the ``SIMcheck_.jar`` file
that appears in the target directory should be copied to an ImageJ plugin
folder. SIMcheck will appear in the menu after restarting the ImageJ
application.

Layout & Documentation
----------------------

API javadocs are generated and can be found in ``target/apidocs``. Briefly,
the main ``SIMcheck_ class`` produces a dialog that runs the other check
plugins. The ImageJ menu entries are defined in the ``plugins.config``
file in ``src/main/resources/``, where a ``SIMcheck`` subdirectory contains
custom Look-Up Tables. In addition to the main SIMcheck dialog and plugins that
appear in the SIMcheck menu (named starting with ``Raw_`` for raw data checks,
``Rec_`` for reconstructed data checks, ``Cal_`` for calibration checks and
``Util_`` for utility plugins) , there are a number of supporting classes:

``I1l``
    class containing static utility methods used throughout other classes

``DFT1D``
    hand-coded, multithreaded 1D DFT
    
``FFT2D``
    extension of ImageJ's FHT class, adding new methods (win func, phase..)

``OrthoReslicer``
    customized, stripped-down version of ImageJ's Slicer plugin

``Radial_Profile``
    customized version of Paul Baggethun's Radial Profile plugin

``TestData``
    defines paths to test data for manual ``.main()`` testing of plugins

``J``
    a class containing static utility methods not specific to ImageJ

``ResultSet``
    a container for results (images, statistics and information strings)
    with code for auto-generating reports

Testing
-------

A limited JUnit test suite is provided in ``src/main/test``, and most classes
define a package-private ``.test()`` method for testing class internals
using only code-generated data. This is in contrast to the ``.main()`` plugin
methods intended for manual testing during development, which access real data
using paths defined in the ``TestData`` class.

.. [#] Earlier versions of the project included and Ant build script and it
   was required, before building the project, to make a ./lib/ directory
   containing a soft link to the ij.jar from the desired ImageJ version, as
   well as a soft link to junit.jar. The built result was be copied to
   ./plugins/ which was intended to be a soft-link this to the local ImageJ
   plugins folder. Typing "ant" built the default (all) target, and after
   restarting ImageJ or selecting Help->Refresh Menus SIMcheck would appear
   in the menu.
