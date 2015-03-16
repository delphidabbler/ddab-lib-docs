#summary Description of the TPJWdwState.Section property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Section property =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJWdwState TPJWdwState]_

{{{
property Section: string;
}}}

== Description ==

This property names the section within the ini file in which the window's size, position and state information is recorded.

Setting this property to the empty string causes a default value to be used. This value is `'Window_'` followed by the name of the form (e.g. `'Window_Form1'`).