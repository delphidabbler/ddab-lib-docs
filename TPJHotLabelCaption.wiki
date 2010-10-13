#summary Description of the TPJHotLabel.Caption property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Caption property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property Caption: TCaption;
}}}

== Description ==

This property specifies a text string that that may be displayed in the label.

Use _Caption_ to set the text displayed in the label. If the _[TPJHotLabelCaptionIsURL CaptionIsURL]_ property is `True` then the _Caption_ and _[TPJHotLabelURL URL]_ properties are equivalent, i.e. assigning a value to one will also assign the the same value to the other. This makes it easy to display the URL in the label itself. To display text on the label that is different to the URL make sure that the _[TPJHotLabelCaptionIsURL CaptionIsURL]_ property is `False`.

For reasons of backward compatibilty with earlier versions of the component the default behaviour is for the _Caption_ property to display the URL (i.e. _[TPJHotLabelCaptionIsURL CaptionIsURL]_ is `True` by default).

If the _[TPJHotLabelValidateURL ValidateURL]_ and _[TPJHotLabelCaptionIsURL CaptionIsURL]_ properties are both `True` then any text assigned to the _Caption_ property must be a valid URL or an exception will be raised.

_Caption_'s behaviour with regard to accelerator characters and the ampersand (`&`) is identical to that of _TLabel_. See Delphi help for further information.

The default value of the _Caption_ property is the default URL `http://localhost/`.
