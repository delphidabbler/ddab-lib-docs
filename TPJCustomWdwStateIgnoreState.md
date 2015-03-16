#summary Description of the TPJCustomWdwState.IgnoreState property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IgnoreState property =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJCustomWdwState TPJCustomWdwState]_

{{{
property IgnoreState: Boolean;
}}}

== Description ==

*PROPERTY DEPRECATED*

Determines whether the window's saved state (maximised, normal or minimised) is applied on restoration.

Setting _!IgnoreState_ to true is the same as including `woIngoreState` in the _[TPJCustomWdwStateOptions Options]_ property, and setting _!IgnoreState_ false is the same as excluding `woIngoreState` from _[TPJCustomWdwStateOptions Options]_.

_!IgnoreState_ is provided for backwards compatibility purposes only and may be removed from future releases.
