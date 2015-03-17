# CaptionIsURL property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

```pascal
property CaptionIsURL: Boolean;
```

## Description ##

The _CaptionIsURL_ property is used to determine whether the _[Caption](TPJHotLabelCaption.md)_ property displays the URL assigned to the _[URL](TPJHotLabelURL.md)_ property or whether it can display descriptive text.

Set _CaptionIsURL_ to `True` to link the _[Caption](TPJHotLabelCaption.md)_ property to the _[URL](TPJHotLabelURL.md)_ property - so that assigning one property also assigns the other. This makes it easy to display a URL in the label without assigning two properties with the same value.

Setting _CaptionIsURL_ to `False` enables any text to be assigned to the _[Caption](TPJHotLabelCaption.md)_ property. This permits descriptive text to be displayed in the label that accesses the separately stored URL when the label is clicked. **Tip:** to give the user visual feedback of the actual URL when the mouse hovers over the label set the _[HintStyle](TPJHotLabelHintStyle.md)_ property to `hsURL`.

The default value of _CaptionIsURL_ is `True`.