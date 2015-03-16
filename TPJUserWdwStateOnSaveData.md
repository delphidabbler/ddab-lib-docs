#summary Description of the TPJUserWdwState.OnSaveData method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnSaveData event =

*Project:* [WindowStateComponents Window State Components].

*Unit:* _PJWdwState_. 

*Class:* _[TPJUserWdwState TPJUserWdwState]_

{{{
type
  TPJWdwStateSaveData = procedure(
    Sender: TObject; const Data: TPJWdwStateData
  ) of object;

property OnSaveData: TPJWdwStateSaveData;
}}}

== Description ==

_!OnSaveData_ is triggered when the component is saving the window's size, position and state and needs to store the information in persistent storage.

The user must handle this event by writing the data passed in the fields of the _Data_ parameter to persistent storage. The _Data_ parameter is a record of type _[TPJWdwStateData TPJWdwStateData]_.

*See Also:*
  _[TPJUserWdwStateOnReadData OnReadData]_ event.
