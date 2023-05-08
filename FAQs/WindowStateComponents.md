# Windows State Components FAQ

This page has some frequently asked questions about the DelphiDabbler [Window State Components](https://delphidabbler.com/software/wdwstate). You can also try the components' [documentation](https://delphidabbler.com/url/wdwstate-docs).

## Contents

1. [Why does my form always centre itself on the screen even when TPJWdwState saved the old position?](#faq-1)
2. [Why don't the components work if they are created at run time?](#faq-2)
3. [Why does the TPJRegWdwSate.RootKey property display numbers in the object inspector rather than symbols like HKEY_LOCAL_MACHINE?](#faq-3)
4. [Where does TPJWdwState store my window's state data?](#faq-4)
5. [Why does TPJWdwState raise a "can't write file" exception when it is saving the window state?](#faq-5)

----

## FAQ 1

**Why does my form always centre itself on the screen even when TPJWdwState saved the old position?**

First note that this problem applies to all the window state components, not just `TPJWdwState`.

This is very probably happening because the form's `Position` property is set to something like `poScreenCenter`. For the Window State Components to work the `Position` property **must** be set to `poDesigned`.

Delphi seems to act on the `Position` property after the window state component has set the form size and position, overriding any changes in size and / or made by the component.

I suppose the components could be modified to allow the `Position` property to be overruled. If this would mean the components would change the form's `Position` property I think that's bad practise. I know there's some disagreement amongst users about this design choice, but I'm sticking with it unless someone can come up with some code to work round the problem without changing the `Position` property permanently.

## FAQ 2

**Why don't the components work if they are created at run time?**

You are probably using the standard `Create` constructor to create the component. This does not work properly if called dynamically since it depends on the `Loaded` method being called to complete instantiation of the component. `Loaded` is only called for components placed on the form at design time.

To get round this problem an alternative constructor named `CreateStandAlone` is provided. Call `CreateStandAlone` instead of `Create` and everything should work properly. A reference to the form that the component is to work with must be passed to `CreateStandAlone` as a parameter.

Here's some sample code you could put in your form's `OnCreate` and `OnDestroy` event handlers to restore and save the form's position:


```pascal
procedure Form1.FormCreate(Sender: TObject);
begin
  fWdwState := TPJWdwState.CreateStandAlone(Self);
  fWdwState.Restore;
end;

procedure TForm1.FormDestroy(Sender: TObject);
begin
  fWdwState.Save;
  // No need to free fWdwState: the form does this automatically when it is freed
end;
```


This code assumes you are using a `TPJWdwState` component that has been declared as a field of the form and named `fWdwState`. The code works for any of the window state components.

> **Note:** `CreateStandAlone` was added in v4.3.

## FAQ 3

**Why does the TPJRegWdwSate.RootKey property display numbers in the object inspector rather than symbols like HKEY_LOCAL_MACHINE?**

Symbols such as `HKEY_LOCAL_MACHINE` are simply constants representing the numbers that identify different root keys. Here's a list of the possible root keys:

Constant                | Hex value | Decimal Value
------------------------|-----------|--------------
`HKEY_CLASSES_ROOT`     | 80000000  | 2147483648
`HKEY_CURRENT_USER`     | 80000001  | 2147483649
`HKEY_LOCAL_MACHINE`    | 80000002  | 2147483650
`HKEY_USERS`            | 80000003  | 2147483651
`HKEY_PERFORMANCE_DATA` | 80000004  | 2147483652
`HKEY_CURRENT_CONFIG`   | 80000005  | 2147483653
`HKEY_DYN_DATA`         | 80000006  | 2147483654

The object inspector is displaying the actual number because it doesn't know about the constant names. You need to enter the correct decimal or hex number from the above table. Prefix hex numbers with a `$` character.

## FAQ 4

**Where does TPJWdwState store my window's state data?**

The component stores the information in an ini file. Where the file is located changed at version 5.5.0 of the `PJWdwState` unit. From v5.5.0 more options are available and the defaults are more suitable to modern applications whereas in v5.4.2 and earlier there are fewer options and the defaults are not particularly well chosen.

### Version 5.5.0 and later

There are various possibilities depending on how you have configured `TPJWdwState`'s  `IniFileName` and `IniRootDir` properties.

You should read the documentation of these properties to get an explanation then come back here and look at the table below that gives examples of various property values for a program with full path name `C:\SamplePath\Example.exe`:

IniFileName property value  | IniRootDir property value | Ini file path
----------------------------|---------------------------|--------------
_Empty string_              | `rdAppDataDir`            | `%appdata%\DelphiDabbler\WindowStateStore\Example.ini`
_Empty string_              | `rdProgramDataDir`        | `%programdata%\DelphiDabbler\WindowStateStore\Example.ini` |
_Empty string_              | `rdExeDir`                | `C:\SamplePath\Example.ini`
_Empty string_              | `rdWindowsDir`            | `%systemroot%\Example.ini`
`Config.ini`                | `rdAppDataDir`            | `%appdata%\DelphiDabbler\WindowStateStore\Config.ini`
`Config.ini`                | `rdProgramDataDir`        | `%progdata%\DelphiDabbler\WindowStateStore\Config.ini`
`Config.ini`                | `rdExeDir`                | `C:\SamplePath\Config.ini`
`Config.ini`                | `rdWindowsDir`            | `%systemroot%\Config.ini`
`MyConfigDir\Config.ini`    | `rdAppDataDir`            | `%appdata%\MyConfigDir\Config.ini`
`MyConfigDir\Config.ini`    | `rdProgramDataDir`        | `%progdata%\MyConfigDir\Config.ini`
`MyConfigDir\Config.ini`    | `rdExeDir`                | `C:\SamplePath\MyConfigDir\Config.ini`
`MyConfigDir\Config.ini`    | `rdWindowsDir`            | `%systemroot%\MyConfigDir\Config.ini`
`C:\MyConfigDir\Config.ini` | _Any value_               | `C:\MyConfigDir\Config.ini`

Note that in the above table `%appdata%` is the current user's application data directory, `%progdata%` is the system's common application data directory and `%systemroot%` is the Windows directory.

If you have configured `TPJWdwState` to automatically restore window state at run time (i.e. `AutoSaveRestore` property is `True`) and you also want to set the ini file name and / or root directory at run time, setting the `IniFileName` and `IniRootDir` properties won't work because the component may try to read the ini file before the property is set! You can get round this problem by handling the `OnGetIniDataEx` event and assigning the required values to the event handler's `AIniFileName` and `AIniRootDir` parameters.

### Version 5.4.2 and earlier

There are various possibilities depending on how you have configured `TPJWdwState`'s `IniFileName` property:

* If the property is not set (the default) then the file name will be the same as the program exe file name except that the extension will be changed from .exe to .ini. The ini file will be stored in the same directory as the program file. This is **not recommended** because current Windows OSs will possibly deny write access to the program file's directory.

* If the property is set to a file name that does not include any path information, e.g. `Config.ini`, then the ini file will have the given name and will be placed in the Windows directory. Again this is **not recommended** because it is likely the program will not have permission to write to the Windows directory.

* If the property is set to a fully specified file name of the ini file then that file and path will be used. This is not always convenient since the path is not always known at design time. You can get round this by setting the property at run time, but even this may not work if the `AutoSaveRestore` property is `True` because the component may try to read the ini file before the property is set!

Examples:

IniFileName property value  | Ini file name                       | Notes
----------------------------|-------------------------------------|------
not set (empty string)      | `C:\PathToProg\MyProg.ini`          | Assumes that the program is named `MyProg.exe` and is running from the `C:\PathToProg` directory.
`Config.ini`                | `C:\Windows\Config.ini`             | Assumes that `C:\Windows` is the system's Windows directory.
`MyConfigDir\Config.ini`    | `C:\Windows\MyConfigDir\Config.ini` | Assumes that `C:\Windows` is the system's Windows directory. Note that `C:\Windows\MyConfigDir` must exist.
`C:\MyConfigDir\Config.ini` | `C:\MyConfigDir\Config.ini`         | Note that `C:\MyConfigDir` must exist.

It is obvious that none of the above are ideal and it is for this reason that the `OnGetIniData` event was added.

You can handle this event to set the ini file name at run time (along with the name of the ini file section to use if you wish). This overrides the value of the `IniFileName` property and is guaranteed to be called before the component tries to read or write the ini file.

Here's an example of handling `OnGetIniData` that places the ini file in the `DelphiDabblerEg` sub-directory of the current user's application data directory. It also ensures that the directory exists. The example assumes that the `TPJWdwState` component is named `PJWdwState1` and form containing it is `Form1`. It also requires the `ShlObj` and `SysUtils` units and uses the `SpecialFolderPath` routine from the Code Snippets Database.

```pascal
procedure TForm1.PJWdwStateGetIniData(Sender: TObject;
  var IniFilename, Section: string);
var
  Dir: string;
begin
  Dir := IncludeTrailingPathDelimiter(SpecialFolderPath(CSIDL_APPDATA))
    + '/DelphiDabblerEg';
  ForceDirectories(Dir);
  IniFilename := Dir + '\Config.ini';
end;
```

## FAQ 5

**Why does TPJWdwState raise a "can't write file" exception when it is saving the window state?**

This exception gets raised when the ini file it uses to record window state information can't be created or can't be written to. This is usually because the program user does not have permission to write to the directory containing the ini file. In versions before v5.5.0 this exception may also be raised if any of the directories in the ini file's path do not exist (v5.5.0 and later try to create non-existant directories).

You should change the path to the ini file using either the `IniFileName` property or the `OnGetIniData` event.

Note that this exception can be raised when you call the `TPJWdwState`'s `Save` method or, if the `AutoSaveRestore` property is true, when the program terminates.
