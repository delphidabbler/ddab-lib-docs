#summary Description of the TPJHotLabel.VisitedFont property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !VisitedFont property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

*Introduced:* v2.2

{{{
property VisitedFont: TFont;
}}}

== Description ==

_!VisitedFont_ controls the attributes font used to display the label when the _[TPJHotLabelVisited Visited]_^[v2.2]^ property is `True` and the label is not highlighted.

To change to a new font, specify a new _TFont_ object. To modify a font, change the value of the _Color_, _Height_, _Name_, _Pitch_, _Size_, or _Style_ of the _TFont_ object.

The property defaults to the same font as the _[TPJHotLabelFont Font]_ property but with the colour changed to `clBlue`.

It is recommended that only the colour and certain styles of the font are altered and the font size and name remain unchanged so that the label does not grow or shrink when changing to and from the visited state or when highlighted.