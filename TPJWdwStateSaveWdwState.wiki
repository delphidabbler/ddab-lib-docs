#summary Description of the TPJWdwState.SaveWdwState method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !SaveWdwState method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJWdwState TPJWdwState]_

{{{
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); override;
}}}

== Description ==

_!SaveWdwState_ is used to write a window's size, position and state to an ini file.

This protected method is overridden by _[TPJWdwState TPJWdwState]_ to save the window's state, size and position information to an in file. Before saving the data _!SaveWdwState_ triggers the _[TPJWdwStateOnGetIniData OnGetIniData]_ event (or, from v5.5, _[TPJWdwStateOnGetIniDataEx OnGetIniDataEx]_) to enable the user to change the location and name of the ini file and the section within it where the data is to be saved.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the _State_ parameter is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. 

This method is called by the _[TPJWdwStateSave Save]_ method.