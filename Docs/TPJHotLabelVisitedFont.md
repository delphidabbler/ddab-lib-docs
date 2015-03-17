# VisitedFont property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

**Introduced:** v2.2

```pascal
property VisitedFont: TFont;
```

## Description ##

_VisitedFont_ controls the attributes font used to display the label when the _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> property is `True` and the label is not highlighted.

To change to a new font, specify a new _TFont_ object. To modify a font, change the value of the _Color_, _Height_, _Name_, _Pitch_, _Size_, or _Style_ of the _TFont_ object.

The property defaults to the same font as the _[Font](TPJHotLabelFont.md)_ property but with the colour changed to `clBlue`.

It is recommended that only the colour and certain styles of the font are altered and the font size and name remain unchanged so that the label does not grow or shrink when changing to and from the visited state or when highlighted.