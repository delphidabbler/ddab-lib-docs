# HighlightURL property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

```pascal
property HighlightURL: Boolean;
```

## Description ##

_HighlightURL_ determines whether the label's text is highlighted when the mouse passes of the control.

When this property is `True` the label's text is highlighted using the font defined by the _[HighlightFont](TPJHotLabelHighlightFont.md)_ property. When _HighlightURL_ is `False` the text is not highlighted and the _[HighlightFont](TPJHotLabelHighlightFont.md)_ property is ignored.

This property is provided to maintain backward compatibility with previous versions of the component that did not support text highlighting. The default value of the property is `False` so that by default the control does not highlight its text.