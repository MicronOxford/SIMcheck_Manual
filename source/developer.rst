Developer Documentation
=======================

The SIMcheck project uses Apache Maven as a build and dependency management
tool. After the ``mvn package`` phase, the ``SIMcheck_.jar`` file that
appears in the target directory should be copied to an ImageJ plugin folder.
SIMcheck will appear in the menu after restarting the ImageJ application.

Earlier versions of the project included and Ant build script and it was
required, before building the project, to make a ./lib/ directory containing
a soft link to the ij.jar from the desired ImageJ version, as well as a soft
link to junit.jar. The built result was be copied to ./plugins/ which was
intended to be a soft-link this to the local ImageJ plugins folder. Typing
"ant" built the default (all) target, and after restarting ImageJ or
selecting Help->Refresh Menus SIMcheck would appear in the menu.
