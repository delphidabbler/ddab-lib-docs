#summary Description of the TPJWdwState.Restore method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Restore method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJWdwState TPJWdwState]_

{{{
procedure Restore;
}}}

== Description ==

This method restores the size and position of the owning form's window according to value saved in a specified section of an ini file. If the ini file or section do not exist then this method has no effect.

Various values of the _[TPJCustomWdwStateOptions Options]_ property may cause either the saved size or state to be ignored or for the window to be repositioned (and possibly resized) to fit within the desktop's work area.

If the _[TPJCustomWdwStateAutoSaveRestore AutoSaveRestore]_ property is true _Restore_ is called automatically when the window is created.

== Remarks ==

=== v5.4.2 and earlier ===

The ini file name is determined by the _[TPJWdwStateIniFileName IniFileName]_ property and the section within it that contains the window state data is determined by the _[TPJWdwStateSection Section]_ property.

Any _[TPJWdwStateOnGetIniData OnGetIniData]_ event handler can override any of these property values.

=== v5.5.0 and later ===

The ini file name is determined by both the _[TPJWdwStateIniRootDir IniRootDir]_ and _[TPJWdwStateIniFileName IniFileName]_ properties and the section within it that contains the window state data is determined by the _[TPJWdwStateSection Section]_ property.

Any _[TPJWdwStateOnGetIniDataEx OnGetIniDataEx]_ or _[TPJWdwStateOnGetIniData OnGetIniData]_ event handler can override any of these property values.