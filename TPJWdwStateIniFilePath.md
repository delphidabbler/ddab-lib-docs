#summary Description of the TPJWdwState.IniFilePath method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IniFilePath method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJWdwState TPJWdwState]_

*Introduced:* v5.5

{{{
function IniFilePath: string
}}}

== Description ==

This method returns the fully specified file name of the ini file used to store window state information.

The return value depends on the the values of the _[TPJWdwStateIniRootDir IniRootDir]_ and _[TPJWdwStateIniFileName IniFileName]_ properties as modified by the values returned from any _[TPJWdwStateOnGetIniDataEx OnGetIniDataEx]_ or _[TPJWdwStateOnGetIniData OnGetIniData]_ event handlers.