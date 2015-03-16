#summary Description of the TPJUserWdwState.Save method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Save method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJUserWdwState TPJUserWdwState]_

{{{
procedure Save;
}}}

== Description ==

This method saves the state, size and position of the owning form's window to persistent storage. The _[TPJUserWdwStateOnSaveData OnSaveData]_ event is triggered by this method. The user must handle the event by saving the provided window state data.

For MDI child forms the window's top and left coordinates are relative to the MDI main form's client area. For other, top level, windows the coordinates are relative to the screen.

If the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property is true then _Save_ is called automatically when the window is destroyed.
