#summary Description of the TPJHotLabel.HighlightFont property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !HighlightFont property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property HighlightFont: TFont;
}}}

== Description ==

This property controls the appearance of the label when the mouse passes over it.

A _[TPJHotLabel TPJHotLabel]_ can highlight its text when the mouse passes over the control. The font that is used to highlight the text is determined by the _!HighlightFont_ property. The property defaults to the same font as the _[TPJHotLabelFont Font]_ property but with the colour changed to `clRed`.

Note that the highlighting only takes place when the _[TPJHotLabelHighlightURL HighlightURL]_ property is `True`.

It is recommended that only the colour and certain styles of the font are altered and the font size and name remain unchanged so that the label does not grow and shrink when the cursor passes over it. See the [HotLabelExample1 highlighting example] for details of two suitable designs.