#summary Description of the TPJRegWdwState.SaveWdwState method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !SaveWdwState method =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJRegWdwState TPJRegWdwState]_

{{{
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); override;
}}}

== Description ==

_!SaveWdwState_ is used to write a window's size, position and state to the registry.

This protected method is overridden by _[TPJRegWdwState TPJRegWdwState]_ to save the window's state, size and position information to the registry. Before saving the data _!SaveWdwState_ triggers either the _[TPJRegWdwStateOnGetRegData OnGetRegData]_ or the _[TPJRegWdwStateOnGetRegDataEx OnGetRegDataEx]_*^v5.6^* event to enable the user to change the registry key to use to save the state data.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the _State_ parameter is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. 

This method is called by the _[TPJRegWdwStateSave Save]_ method.