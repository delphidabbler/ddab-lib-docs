# About Box Component #

This project contains one unit - _PJAbout_ that implements a non-visual component, _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_, that encapsulates an "About" dialogue box.

When displayed the about box appears like this (screen shot taken on Windows Vista):

![DelphiDabbler About Box component screenshot](Images/aboutbox.png)

The text displayed in the about box can be set using properties exposed by the component, or can be extracted from version information using a linked DelphiDabbler Version Information Component.

The dialogue's position can be specified relative to the screen, desktop or parent application. There is a single close button whose appearance and position is customised. The About box also displays the program's icon. Finally, the dialogue box's font can be altered.

The code is Unicode compatibale when compiled on Unicode enabled versions of Delphi.

The _PJAbout_ unit also defines the _TPJAboutBoxForm_ form class that implements the actual about box. This class should not be accessed directly and is un-documented.

## Documentation ##

The component is fully documented [online](TPJAboutBoxDlg.md).

## Demo program ##

A demo program is included in the download that can be used to exercise the component.

## Compatibility with earlier versions ##

_TPJAboutBoxDlg_ is believed to compile on all Win32 versions of Delphi, but the latest version has been tested only on Delphi 7 and Delphi 2007 through to XE3. It is assumed to work on other versions. Delphi 1 support was dropped at v3.5.

The component is compatible with the Delphi 64 bit Windows compiler and can be included in 64 bit VCL packages.

The unit name changed to _PJAbout_ at release 3. Programs using earlier releases will need to be modified (or to have an alias set in Delphi's Project Options) before being recompiled using the new version.

## Download ##

You can get this unit's source code in two ways:

1. By checking out code from project's subversion repository. Stable releases can be found at https://sourceforge.net/p/ddablib/code/HEAD/tree/tags/projects/aboutbox/ while the current development code is at https://sourceforge.net/p/ddablib/code/HEAD/tree/trunk/projects/aboutbox/. Follow the instructions on those pages for details of how to check out. You can find installation instructions in a file named `ReadMe.htm` in the `Docs` directory.

2. By downloading a release .zip file from [SourceForge](https://sourceforge.net/projects/ddablib/files/aboutbox/). The .zip file contains a read-me file (`ReadMe.htm`) that tells you how to install the component into the Delphi IDE. Always choose the most recent version unless you have good reason not to.

***Note:*** *Do not try to download source code from DelphiDabbler.com - downloadable files are in the process of being removed from that site now that they are available on SourceForge.*

### Required component ###

_TPJAboutBoxDlg_ requires that a DelphiDabbler [Version Information Component](VersionInformationComponent.md) is installed in order to compile.

## Issues ##

If you wish to report a bug please complete a ticket in the [issue tracker](https://sourceforge.net/p/ddablib/tickets/) on SourceForge. Because the issue tracker is shared between several DelphiDabbler Code Library projects, you should add a label named `aboutbox` to your ticket otherwise it may not be clear which project your bug relates to.

***Please Note:*** *Requests for new features are no longer being accepted for this component.*

## Change Log ##

A change log will be included in downloaded zip files. In the Subversion repository change logs can be found in the file `ChangeLog.txt` in the `Docs` directory.

The latest edition of the change log can be found [here](https://sourceforge.net/p/ddablib/code/HEAD/tree/trunk/projects/aboutbox/Docs/ChangeLog.txt).

## License ##

The DelphiDabbler About Box Component is copyright &copy; 1998-2014 Peter Johnson (@delphidabbler) and is released under the terms of the [Mozilla Public License v2.0](http://www.mozilla.org/MPL/2.0/).

**Links:**

  * Back to [Wiki Home Page](Welcome.md)
  * [About Box Component Web Page](https://delphidabbler.com/software/aboutbox).
