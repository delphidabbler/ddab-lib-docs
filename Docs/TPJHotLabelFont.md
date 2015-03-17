# Font property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

```pascal
property Font: TFont;
```

## Description ##

_Font_ controls the attributes font used to display the label when it is not highlighted.

<sup>[v2.2]</sup> At run-time the _Font_ property is only displayed if the _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> property is `False`, otherwise the label's display font is that specified by the _[VisitedFont](TPJHotLabelVisitedFont.md)_<sup>[v2.2]</sup> property.

To change to a new font, specify a new _TFont_ object. To modify a font, change the value of the _Color_, _Height_, _Name_, _Pitch_, _Size_, or _Style_ of the _TFont_ object.

The default value of _[TPJHotLabel](TPJHotLabel.md)_'s _Font_ property is different from that of the inherited property: the font _Color_ defaults to `clNavy` and the font _Style_ defaults to `[fsUnderline]`. The other attributes are those of the parent control when the component was first dropped on the form.

Since the default font attributes are likely to be different to those of the inherited _Font_ property the _[ParentFont](TPJHotLabelParentFont.md)_ property defaults to `False` rather than `True` in the ancestor property. This means that any change to the parent control's font will not be echoed in this component.

Note that _Font_ is always used as the component's display font at design time.