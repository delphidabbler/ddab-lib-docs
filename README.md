# DelphiDabbler Code Library

The DelphiDabbler Code Library contains various useful and re-usable Delphi components, units and IDE extensions, arranged in sub-projects. All were originally published on [DelphiDabbler.com](http://www.delphidabbler.com/).

Many of the components and classes are stable and have been in development for a number of years. For details of each sub-project see [this summary](Docs/Welcome.md).

The project contains these components, classes and IDE extensions:

| Project | Documentation | Releases | More Info |  Platforms | Framework |
| ------- | ------------- | -------- | --------- | --------- | --------- |
| About Box Component | [GitHub](Docs/AboutBoxComponent.md)<br>WinHelp | [SourceForge](https://sourceforge.net/projects/ddablib/files/aboutbox/) | [Website](http://www.delphidabbler.com/software/aboutbox) | Win32<br>Win64 | VCL<br><strike>FMX</strike> |
| Clipboard Viewer Component | [GitHub](Docs/ClipboardViewerComponent.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/cbview/) | [Website](http://www.delphidabbler.com/software/cbview) | Win32<br>Win64 | VCL<br><strike>FMX</strike> |
| Console Application Runner Classes | [GitHub](Docs/ConsoleApp.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/consoleapp/) | [Website](http://www.delphidabbler.com/software/consoleapp) | Win32<br>Win64 | RTL |
| Drop Files Components | [GitHub](Docs/DropFilesComponents.md)<br>WinHelp | [SourceForge](https://sourceforge.net/projects/ddablib/files/dropfiles/) | [Website](http://www.delphidabbler.com/software/dropfiles) | Win32<br>Win64 | VCL<br><strike>FMX</strike> |
| Environment Variables Unit | [GitHub](Docs/EnvVars.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/envvars/) | [Website](http://www.delphidabbler.com/software/envvars) | Win32<br>Win64 | VCL<br>FMX |
| Extended String Property Editor | [GitHub](Docs/StringPE.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/stringpe/) | [Website](http://www.delphidabbler.com/software/stringpe) | Win32<br><strike>Win64</strike> | IDE |
| Fractions Unit *(beta)* | [GitHub](Docs/Fractions.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/fractions/) | [Website](http://www.delphidabbler.com/software/fractions) | Win32<br>Win64 | RTL |
| Hot Label Component | [GitHub](Docs/HotLabelComponent.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/hotlabel/) | [Website](http://www.delphidabbler.com/software/hotlabel) | Win32<br>Win64 | VCL<br><strike>FMX</strike> |
| I/O Utility Classes | [GitHub](Docs/IOUtils.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/ioutils/) | [Website](http://delphidabbler.com/software/ioutils) | Win32<br>Win64 | RTL |
| MD5 Message Digest Class | [GitHub](Docs/MD5.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/md5/) | [Website](http://www.delphidabbler.com/software/md5) | Win32<br>Win64 | RTL |
| Message Dialogue Components | [GitHub](Docs/MessageDialogComponents.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/msgdlg/) | [Website](http://www.delphidabbler.com/software/msgdlg)| Win32<br>Win64 | VCL<br><strike>FMX</strike> |
| Resource File Unit | [GitHub](Docs/ResFileUnit.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/resfile/) | [Website](http://www.delphidabbler.com/software/resfile) | Win32<br>Win64 | RTL |
| Shell Folders Unit | [GitHub](Docs/ShellFoldersUnit.md)<br>WinHelp | [SourceForge](https://sourceforge.net/projects/ddablib/files/shellfolders/) | [Website](http://www.delphidabbler.com/software/shellfolders) | Win32<br>Win64 | VCL<br><strike>FMX</strike> |
| Stream Extension Classes | [GitHub](Docs/StreamExtensionClasses.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/streams/) | [Website](http://www.delphidabbler.com/software/streams) | Win32<br>Win64 | RTL |
| System Information Unit | [GitHub](Docs/SystemInformationUnit.md) | [SourceForge](https://sourceforge.net/projects/ddablib/files/sysinfo/) | [Website](http://www.delphidabbler.com/software/sysinfo) | Win32<br>Win64 | RTL |
| Version Information Component | [GitHub](Docs/VerInfo.md)<br>WinHelp | [SourceForge](https://sourceforge.net/projects/ddablib/files/verinfo/) | [Website](http://www.delphidabbler.com/software/verinfo) | Win32<br>Win64 | VCL<br>FMX |
| Window State Components | [GitHub](Docs/WindowStateComponents.md)<br>WinHelp | [SourceForge](https://sourceforge.net/projects/ddablib/files/wdwstate/) | [Website](http://www.delphidabbler.com/software/wdwstate) | Win32<br>Win64 | VCL<br><strike>FMX</strike> |

The **Documentation** column contains links to the documentation for the project.

The **Releases** column contains links to the project's directory on the *SourceForge* file manager from where zip files containing releases can be downloaded. That directory's read-me file provides information about the available downloads.

The **More Info** column has links that take you to the library project's page on DelphiDabbler.com.

The **Platforms** column notes the platforms that the project is compatible with. *Win32* is 32 bit Windows and *Win64* is 64 bit Windows. Struck out items, like *<strike>Win64</strike>*, indicate that the code is not compatible with the platform. IDE extensions are only ever 32 bit compatible. **Note:** No projects in this library have been tested on non-Windows platforms.

The **Framework** column notes whether the project is compatible with either the VCL or FireMonkey, has no dependencies, or is an IDE extension. The following abbreviations are used:

  * *RTL* - requires only the Delphi run time library, so has no dependencies on either the VCL and FMX frameworks and can be used with either or none.
  * *VCL* - compatible with the Visual Component Library framework.
  * *FMX* - compatible with the FireMonkey framework.
  * *IDE* - an IDE extension.

Struck out frameworks such as *<strike>FMX</strike>* are not supported by the project.

## FAQs

Frequently asked questions for some of the Code Library projects are available and listed on the [FAQs](FAQs/FAQs.md) page.

## Library News

You can get the latest news about the Code Library by following the [DelphiDabbler Blog](https://delphidabbler.blogspot.com/).

## License

All the code in the library now uses the Mozilla Public License v2.0 (MPL 2.0). Earlier versions may use the Mozilla Public License v1.1.

Note that the documentation is published under a different license: [see below](#documentation-license).

## About this documentation

### A little history

The documentation started out as a wiki on Google Code, maintained in a Subversion repository as a branch of the DelphiDabbler Code Library Project. The wiki branch was extracted from the Subversion repository and converted to Git as at commit 1d1404b. The Git repository was placed on GitHub in the `delphidabbler/ddab-lib-docs` project.

Development continued directly on the `master` branch until commit 39b9e5a when the GitFlow development model was adopted.

Development then took place on a `develop` branch. Five releases were made before the GitFlow model was abandoned at commit 0697fcb. The `develop` branch was deleted at commit 979f604 and all the release tags were deleted. The associated change-log file was also removed.

### Development model

Since commit 979f604 a new development model was adopted. Changes are made on branches off `master` and merged into `master` once verified. `master` is pushed to `origin` on GitHub after each merge.

Anyone who would like to contribute can do so using the [GitHub Flow](https://guides.github.com/introduction/flow/) methodology.

### Documentation license

![Creative Commons CC BY-4.0 license image](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)

DelphiDabbler Code Library Documentation by [Peter Johnson](http://en.gravatar.com/delphidabbler) is licensed under a Creative [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

Based on a work at https://github.com/delphidabbler/ddab-lib-docs.

For full details see the `LICENSE` file.
