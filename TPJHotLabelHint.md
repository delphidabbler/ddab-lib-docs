#summary Description of the TPJHotLabel.Hint property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Hint property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property Hint: string;
}}}

== Description ==

_Hint_ contains a text string that can appear when the user moves the mouse over the control.

With one exception, the _Hint_ property of _[TPJHotLabel TPJHotLabel]_ operates in the same way as the inherited property. The exception is that the _[TPJHotLabelHintStyle HintStyle]_ property can change the source of the hint's text. The hint text can be taken from the _[TPJHotLabelURL URL]_ property or a custom value can be supplied by handling the _[TPJHotLabelOnCustomHint OnCustomHint]_ event. If the _[TPJHotLabelURL URL]_ property value is used _Hint_ is ignored. If custom hints are used, the value of the _Hint_ property is supplied to the event handler for modification.
