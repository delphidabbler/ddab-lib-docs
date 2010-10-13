#summary Description of the TPJHotLabel.OnCustomHint event
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnCustomHint event =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
type
  TPJHLCustomHintEvent = procedure(
    Sender: TObject; var HintStr: string
  ) of object;

property OnCustomHint: TPJHLCustomHintEvent;
}}}

== Description ==

_!OnCustomHint_ is an event that enables the user to specify a custom hint to be displayed by the component.

This event is triggered only when the _[TPJHotLabelHintStyle HintStyle]_ property is set to `hsCustom` and a hint is about to be displayed. Handling the event enables the user to specify the text that is displayed in the pop-up hint. The event handler is passed the current _[TPJHotLabelHint Hint]_ property value in the _!HintStr_ parameter. Specify the hint text by setting _!HintStr_ to the required value.

If _[TPJHotLabelHintStyle HintStyle]_ is `hsCustom` and the event is not handled then the value of the _[TPJHotLabelHint Hint]_ property is displayed as normal.

See the [HotLabelExample2 Using the OnCustomHint event] example for one possible use of the _!OnCustomHint_ event.
