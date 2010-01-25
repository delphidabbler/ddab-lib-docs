#summary Description of the TPJCustomWdwState.Save method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Save method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJCustomWdwState TPJCustomWdwState]_

{{{
procedure Save;
}}}

== Description ==

This method saves the state, size and position of the owning form's window.

For MDI child forms the window's top and left coordinates are relative to the MDI main form's client area. For other, top level, windows the coordinates are relative to the screen.

If the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property is true then _Save_ is called automatically when the window is destroyed. If _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ is false then _Save_ must be called from code to save the form's state. A good place to do this is in the form's _!OnDestroy_ event handler.
