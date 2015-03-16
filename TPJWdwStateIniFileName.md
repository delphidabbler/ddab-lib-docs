<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# IniFileName property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

```
property IniFileName: string;
```

## Description ##

This property specifies the name of the ini file that will be used to record the window's size, position and state. The file is accessed by both the _[Restore](TPJWdwStateRestore.md)_ and _[Save](TPJWdwStateSave.md)_ methods.

The default value of the property is the empty string.

The behaviour of the property was changed at v5.5, as described below.

### v5.4.2 and earlier ###

The property can be interpreted in the following ways, depending on its value:

  * _Empty string_: <br>The ini file name is the same as the application, with the extension changed to <code>.ini</code>. The file is placed in the same directory as the application. For example, if the application is <code>C:\Foo\Bar.exe</code> then the full ini file name will be <code>C:\Foo\Bar.ini</code>.</li></ul>

<ul><li><i>Relative path:</i> (e.g. <code>Foo.ini</code> or <code>Foo\Bar.ini</code>)<br>The ini file name is as specified in this property and it is stored in the Windows installation directory. For example an <i>IniFileName</i> property value of <code>Foo.ini</code> might result in an ini file name of <code>C:\Windows\Foo.ini</code> while a property value of <code>Foo\Bar.ini</code> would save window state data in <code>C:\Windows\Foo\Bar.ini</code>.</li></ul>

  * _Absolute path_:<br>The ini file is stored in the specified path.</li></ul>

If the the ini file's directory does not exist an exception will be generated when the component attempts to write to the ini file.<br>
<br>
<h3>v5.5.0 and later ###

The property can be interpreted in the following ways, depending on its value:

  * _Empty string_:<br>The ini file name is the same as the application, with the extension changed to <code>.ini</code>. The file's directory depends on the value of the <i><a href='TPJWdwStateIniRootDir.md'>IniRootDir</a></i> property.</li></ul>

<ul><li><i>Relative path:</i> (e.g. <code>Foo.ini</code> or <code>Foo\Bar.ini</code>)<br>The ini file name is as specified in the property. The file's directory depends on the value of the <i><a href='TPJWdwStateIniRootDir.md'>IniRootDir</a></i> property.</li></ul>

  * _Absolute path_:<br>The ini file is stored in the specified path. The value of the <i><a href='TPJWdwStateIniRootDir.md'>IniRootDir</a></i> property has no effect in this case.</li></ul>

If the ini file's directory does not exist it will be created if possible when the component first attempts to write to the file. If the directory cannot be created an exception will be raised.<br>
<br>
<b>Important note:</b> When updating from earlier versions to v5.5 or later, you should note that <i><a href='TPJWdwState.md'>TPJWdwState</a></i> uses a different file name by default when <i>IniFileName</i> is either a relative path or the empty string. To revert to the original behaviour you need to change the <i><a href='TPJWdwStateIniRootDir.md'>IniRootDir</a></i> property value as follows:<br>
<br>
<ul><li>When <i>IniFileName</i> is the empty string, set <i><a href='TPJWdwStateIniRootDir.md'>IniRootDir</a></i> to <code>rdExeDir</code>.<br>
</li><li>When <i>IniFileName</i> is a relative path, set <i><a href='TPJWdwStateIniRootDir.md'>IniRootDir</a></i> to <code>rdWindowsDir</code>.</li></ul>

<h2>Remarks ##

The value of _IniFileName_ can be overridden at run time if you handle either the _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ or _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ <sup>v5.5</sup> properties. This can be useful when the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is `True` and you want to specify the ini file name at run time. In this case setting _IniFileName_ at run time will not work because the form will be restored before you have an opportunity to change the property value. However the _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ and _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ events are triggered before the form restores, enabling the file name to be specified.

You are strongly recommended **not** to store the ini file in the Windows directory. On Windows Vista and later an attempt to write to the Windows directory may be redirected to the virtual store.

You should not use the directory containing the executable program if it is stored in the _Program Files_ directory (or similar), since you may not have write access to it.

## See Also ##

  * _[Section](TPJWdwStateSection.md)_ property.
  * _[IniRootDir](TPJWdwStateIniRootDir.md)_ <sup>v5.5</sup> property.