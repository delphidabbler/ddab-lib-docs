# HintStyle property #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

**Class:** _[TPJHotLabel](TPJHotLabel.md)_

```pascal
type
  TPJHLHintStyle = (hsNormal, hsURL, hsCustom);

property HintStyle: TPJHLHintStyle;
```

## Description ##

The _HintStyle_ property determines how the text displayed in the component's pop-up hint is derived. There are three possible sources of the hint text:

| **Style** | **Notes** |
|:----------|:----------|
| `hsNormal` | The pop-up hint displays as normal - i.e. the hint's text is taken from the _[Hint](TPJHotLabelHint.md)_ property. |
| `hsURL` | The pop-up hint displays the _[URL](TPJHotLabelURL.md)_ property value. The _[Hint](TPJHotLabelHint.md)_ property is ignored. |
| `hsCustom` | The user can specify a custom hint by handling the _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ event. See the _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ topic for details of how the hint is set in the event handler. If the _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ event is not handled then the hint's text comes from the _[Hint](TPJHotLabelHint.md)_ property as normal. |

Note that no pop-up hint will display unless hints are enabled. This is done by ensuring the inherited _ShowHint_ property is `True`.

The default value of _HintStyle_ is `hsNormal`.