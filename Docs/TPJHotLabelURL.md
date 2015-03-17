# URL property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

```pascal
property URL: string;
```

## Description ##

This property stores the URL that is to be accessed when the label is clicked. The default web browser or mail client are used to display the URL.

If the _[ValidateURL](TPJHotLabelValidateURL.md)_ property is `True` then any value assigned to the _URL_ property must be valid otherwise a _[EPJURLError](EPJURLError.md)_ exception will be raised.

When the _[CaptionIsURL](TPJHotLabelCaptionIsURL.md)_ property is `True` then the value assigned to the _URL_ property is also assigned to the _[Caption](TPJHotLabelCaption.md)_ property and displayed in the label. This makes it easy to display the URL in the label by assigning just one property.

The URL can be displayed in the component's _[Hint](TPJHotLabelHint.md)_ property by setting the _[HintStyle](TPJHotLabelHintStyle.md)_ property to `hsURL`.

The default value of this property is either `http://localhost`<sup>[v2.0]</sup>  or `http://example.com/`<sup>[v2.2]</sup>