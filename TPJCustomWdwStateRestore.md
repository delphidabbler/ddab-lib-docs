#summary Description of the TPJCustomWdwState.Restore method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Restore method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJCustomWdwState TPJCustomWdwState]_

{{{
procedure Restore;
}}}

== Description ==

This method restores the size, position and state of the owning form's window according to saved values.

Various values of the _[TPJCustomWdwStateOptions Options]_ property may cause either the saved size or state to be ignored or for the window to be repositioned (and possibly resized) to fit within the appropriate monitor's desktop work area.

If the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property is true _Restore_ is called automatically when the window is created. If _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ is false then _Restore_ must be called from code to restore the window. The form's _!OnShow_ event handler is a good place to do this.
