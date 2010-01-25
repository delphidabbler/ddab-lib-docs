#summary Description of the TPJCustomWdwState.MinimizeDelay property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !MinimizeDelay property =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJCustomWdwState TPJCustomWdwState]_

{{{
property MinimizeDelay: Integer;
}}}

== Description ==

Sets the delay between displaying a normalised form on screen and minimising it if required.

When a form is to be restored to the minimized state it will flash on screen in its normal state before being minimised. This property determines the delay (in ms) between displaying the normalised form on screen and it being minimised.

The default value is 100.
