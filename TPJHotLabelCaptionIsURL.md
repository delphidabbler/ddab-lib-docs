#summary Description of the TPJHotLabel.CaptionIsURL property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= CaptionIsURL property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property CaptionIsURL: Boolean;
}}}

== Description ==

The _CaptionIsURL_ property is used to determine whether the _[TPJHotLabelCaption Caption]_ property displays the URL assigned to the _[TPJHotLabelURL URL]_ property or whether it can display descriptive text.

Set _CaptionIsURL_ to `True` to link the _[TPJHotLabelCaption Caption]_ property to the _[TPJHotLabelURL URL]_ property - so that assigning one property also assigns the other. This makes it easy to display a URL in the label without assigning two properties with the same value.

Setting _CaptionIsURL_ to `False` enables any text to be assigned to the _[TPJHotLabelCaption Caption]_ property. This permits descriptive text to be displayed in the label that accesses the separately stored URL when the label is clicked. *Tip:* to give the user visual feedback of the actual URL when the mouse hovers over the label set the _[TPJHotLabelHintStyle HintStyle]_ property to `hsURL`.

The default value of _CaptionIsURL_ is `True`.
