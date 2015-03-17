# SubKey property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

```pascal
property SubKey: string;
```

## Description ##

This property defines the subkey under which the window's size, position and state information is stored in the registry. This subkey is stored under the root key defined by the _[RootKey](TPJRegWdwStateRootKey.md)_ or _[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>** property.

To ensure that the sub key is relative to the root and not the current key the subkey should begin with a '\' character.

If the property is set to the empty string then it defaults to

`'\Software\<Program EXE filename>\Window\<Form Name>'`

where `<Program EXE filename>` is the program's executable file name (without the path) and `<Form Name>` is the name of the form on which the _[TPJRegWdwState](TPJRegWdwState.md)_ component is placed. For example, if your program is executed from `C:\MyStuff\MyProg.exe` and the form is named `Form1` then setting _SubKey_ to the empty string causes the property's value to become

`\Software\MyProg.exe\Window\Form1`

The default value of the property is the empty string.