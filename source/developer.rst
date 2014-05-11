Developer Documentation
=======================

The code is arranged in a conventional Maven-like structure and includes
an ant build script that can copy the resulting ``SIMcheck_.jar`` to a local
plugin folder.

Before building the project, first make a ./lib/ directory containing a soft
link to the ij.jar from the desired ImageJ version, as well as a soft link to
junit.jar. The built result will be copied to ./plugins/ so soft-link this to
your ImageJ plugins folder. Type "ant" to build the default (all) target and
restart ImageJ or Help->Refresh Menus
