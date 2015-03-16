#summary Description of the TPJRegWdwState.Save method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Save method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJRegWdwState TPJRegWdwState]_

{{{
procedure Save;
}}}

== Description ==

This method saves the state, size and position of the owning form's window in the registry. The root and sub keys of the registry where the information is saved are specfied by the _[TPJRegWdwStateRootKey RootKey]_ or _[TPJRegWdwStateRootKeyEx RootKeyEx]_*^v5.6^* and _[TPJRegWdwStateSubKey SubKey]_ properties. If the registry key does not exist it is created. If it is not possible to create the key then the information is not saved.

For MDI child forms the window's top and left coordinates are relative to the MDI main form's client area. For other, top level, windows the coordinates are relative to the screen.

If the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property is true then _Save_ is called automatically when the window is destroyed.