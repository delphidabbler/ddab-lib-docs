#summary Description of the TPJHotLabel.URL property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= URL property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property URL: string;
}}}

== Description ==

This property stores the URL that is to be accessed when the label is clicked. The default web browser or mail client are used to display the URL.

If the _[TPJHotLabelValidateURL ValidateURL]_ property is `True` then any value assigned to the _URL_ property must be valid otherwise a _[EPJURLError EPJURLError]_ exception will be raised.

When the _[TPJHotLabelCaptionIsURL CaptionIsURL]_ property is `True` then the value assigned to the _URL_ property is also assigned to the _[TPJHotLabelCaption Caption]_ property and displayed in the label. This makes it easy to display the URL in the label by assigning just one property.

The URL can be displayed in the component's _[TPJHotLabelHint Hint]_ property by setting the _[TPJHotLabelHintStyle HintStyle]_ property to `hsURL`.

The default value of this property is either `http://localhost`^[v2.0]^  or `http://example.com/`^[v2.2]^