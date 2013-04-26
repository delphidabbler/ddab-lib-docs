#summary Description of the TPJRegWdwState.OnGettingRegData method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnGettingRegData event =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJRegWdwState TPJRegWdwState]_

*Introduced:* v5.1

{{{
type
  TPJWdwStateRegAccessEvent = procedure(
    const Reg: TRegistry
  ) of object;

property OnGettingRegData: TPJWdwStateRegAccessEvent;
}}}

== Description ==

_!OnGettingRegData_ allows the user to read additional registry data when the component reads window state information.

The event is triggered just after the window's state information is read from the registry. The event makes available a reference to the _TRegistry_ object used to read the data. This object can be used to read any additional application defined information from the registry.

For example, the size of some controls that appear on the main form may be read. Such data will have been written using the _[TPJRegWdwStateOnPuttingRegData OnPuttingRegData]_ *^v5.1^* event.
