#summary Description of the TPJUserWdwState.SaveWdwState method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !SaveWdwState method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJUserWdwState TPJUserWdwState]_

{{{
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); override;
}}}

== Description ==

_!SaveWdwState_ is used to write a window's size, position and state to persitent storage.

This protected method is overrridden by _[TPJUserWdwState TPJUserWdwState]_ to trigger the _[TPJUserWdwStateOnSaveData OnSaveData]_ event that the user must handle to save the window's state, size and position information.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the _State_ parameter is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. 

This method is called by the _[TPJUserWdwStateSave Save]_ method.
