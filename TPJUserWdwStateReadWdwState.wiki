#summary Description of the TPJUserWdwState.ReadWdwState method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ReadWdwState method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJUserWdwState TPJUserWdwState]_

{{{
procedure ReadWdwState(
  var Left, Top, Width, Height, State: Integer
); override;
}}}

== Description ==

_!ReadWdwState_ is used  used to read a window's size, position and state from persitent storage.

This protected method is overrridden by _[TPJUserWdwState TPJUserWdwState]_ to trigger the _[TPJUserWdwStateOnReadData OnReadData]_ event that the user must handle to read the window's state, size and position information from persistent storage.

The position of the window is returned in the _Left_ and _Top_ parameters, the size in the _Width_ and _Height_ parameters and the state in the _State_ parameter. _State_ is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. The parameters are set to those currently existing for the associated window before calling the method. 

This method is called by the _[TPJUserWdwStateRestore Restore]_ method.
