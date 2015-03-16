#summary Description of the TPJHotLabel.ValidateURL property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= ValidateURL property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property ValidateURL: Boolean;
}}}

== Description ==

This property determines whether the URL stored in the component is validated or not.

Set this property to `True` to cause any value assigned to the _[TPJHotLabelURL URL]_ property to be validated. When _ValidateURL_ is `False` no URLs are validated. Note that setting this property to `True` causes the current URL to be validated immediately.

URLs are validated only by examining the protocol and checking it is supported. Valid protocols are:

  * `http://`
  * `https://`
  * `mailto:`
  * `file:`
  * `ftp://`

If validation fails a _[EPJURLError EPJURLError]_ exception is raised. If this exception is raised while setting _ValidateURL_ to `True` the default URL is stored in the _[TPJHotLabelURL URL]_ property.

When the _[TPJHotLabelCaptionIsURL CaptionIsURL]_ and _ValidateURL_ properties are both `True`, assigning text to the _[TPJHotLabelCaption Caption]_ property also causes the text to be validated. This is because setting the _[TPJHotLabelCaption Caption]_ property in this case automatically updates the _[TPJHotLabelURL URL]_ property.

The default property value is `True`.
