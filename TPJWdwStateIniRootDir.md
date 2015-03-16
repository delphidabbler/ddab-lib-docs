#summary Description of the TPJWdwState.IniRootDir property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IniRootDir property =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_.

*Class:* _[TPJWdwState TPJWdwState]_

*Introduced:* v5.5

{{{
type
  TPJWdwStateIniRootDir = (
    rdWindowsDir, rdExeDir, rdAppDataDir, rdProgramDataDir
  );

property IniRootDir: TPJWdwStateIniRootDir;
}}}

== Description ==

This property determines the root directory to be used for any relative ini file name specified by the _[TPJWdwStateIniFileName IniFileName]_ property.

Possible values are:

|| `rdAppDataDir` || Places the ini file in a _sub-directory_ of the per user application directory, i.e. `%appdata%`. If the file name given by _[TPJWdwStateIniFileName IniFileName]_ does not specify the required sub-directory then the file is stored in the `%appdata%\DelphiDabbler\WindowStateStore` directory. ||
|| `rdProgramDataDir` || Places the ini file in a _sub-directory_ of the common application data directory, i.e. `%programdata%`. If the file name given by _[TPJWdwStateIniFileName IniFileName]_ does not specify the required sub-directory then the file is stored in the `%programdata%\DelphiDabbler\WindowStateStore` directory. ||
|| `rdExeDir` || Places the ini file in the same directory as the program's executable file. This option should not be used for programs stored in the _Program Files_ directory - see below. ||
|| `rdWindowsDir` || Places the ini file in the Windows system directory, i.e. `%systemroot%`. This option should only be used for backwards compatibility with earlier versions of the component - see below. ||


In cases where _[TPJWdwStateIniFileName IniFileName]_ is an absolute path _!IniRootDir_ is ignored.

The full file path of the ini file can be found by calling the _[TPJWdwStateIniFilePath IniFilePath]_ method.

== Remarks ==

The value of _!IniRootDir_ can be overridden at run time if you handle either the _[TPJWdwStateOnGetIniDataEx OnGetIniDataEx]_ event. This can be useful when the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property is `True` and you want to specify the root directory at run time. In this case setting _!IniRootDir_ at run time will not work because the form will be restored before you have an opportunity to change the property value. However the _[TPJWdwStateOnGetIniDataEx OnGetIniDataEx]_ event is triggered before the form restores, enabling the root directory to be specified.

You are strongly recommended *not* to use the `rdWindowsDir` value for _!IniRootDir_ to store the ini file in the Windows directory. On Windows Vista and later an attempt to write to the Windows directory may be redirected to the virtual store. `rdWindowsDir` is provided only for backward compatibility will earlier versions of _[TPJWdwState TPJWdwState]_. See the to get the _[TPJWdwStateIniFileName IniFileName]_ property documentation for more information.

You should set _!IniRootDir_ to `rdExeDir` if the executable program if it is stored in the _Program Files_ directory (or similar), since you may not have write access to it or the file may be redirected to a virtual store. `rdExeDir` is provided mainly for use with portable programs that save confguration data either with, or in sub-directories or, their installation directory.