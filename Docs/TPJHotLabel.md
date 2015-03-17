# TPJHotLabel #

**Project:** [Hot Label Component](HotLabelComponent.md).

**Unit:** _PJHotLabel_.

This component provides a label that can access a user-defined URL when clicked. The URL is displayed in the default browser or email client.

In addition to the properties of _TLabel_, from which this component descends, additional properties for working with URLs are provided. The effect of some of _TLabel_'s properties is modified in _TPJHotLabel_.

### URLs and the Caption ###

The _[URL](TPJHotLabelURL.md)_ property is used for storing the URL to be accessed and the _[Caption](TPJHotLabelCaption.md)_ property can either store descriptive text or can reflect the URL, depending on the value of the _[CaptionIsURL](TPJHotLabelCaptionIsURL.md)_ property. When the _[ValidateURL](TPJHotLabelValidateURL.md)_ property is `True` URLs are automatically validated, raising an exception if invalid.

### Fonts and highlighting ###

The label's _[Font](TPJHotLabelFont.md)_ property defaults to a font based on the parent font at the time the component is dropped on the form, but coloured navy blue. It should be noted that the _[Font](TPJHotLabelFont.md)_ property will not automatically reflect changes in the parent controls's font since _[ParentFont](TPJHotLabelParentFont.md)_ defaults to `False`.

The label can be highlighted when the mouse passes over it. It does this only if the _[HighlightURL](TPJHotLabelHighlightURL.md)_ property is `True`, in which case the _[HighlightFont](TPJHotLabelHighlightFont.md)_ property is used when the mouse is over the label. The value of _[HighlightFont](TPJHotLabelHighlightFont.md)_ is, by default, based on the default font used by the _[Font](TPJHotLabelFont.md)_ property, but with a different colour.

From v2.2 the label can change its appearance to indicate its link has been visited. It does this when its _[Visited](TPJHotLabelVisited.md)_ property is `True`, in which case the _[VisitedFont](TPJHotLabelVisitedFont.md)_ property is used to set the label's font when in its un-highlighted state. _[Visited](TPJHotLabelVisited.md)_ is a writeable property so the user can set its value in code or in the object inspector. Further, if the _[TrackVisits](TPJHotLabelTrackVisits.md)_ property is `True` the label will automatically set _[Visited](TPJHotLabelVisited.md)_ to `True` (and change its appearance) when the label is clicked and the URL is processed without error. The value of _[VisitedFont](TPJHotLabelVisitedFont.md)_ is, by default, based on the default font used by the _[Font](TPJHotLabelFont.md)_ property, but with a different colour.

### The cursor ###

The _[Cursor](TPJHotLabelCursor.md)_ property defaults to `crHandPoint` rather than `crDefault` so that the expected "pointing hand" is displayed over a link.

### Customising hints ###

Useful, customisable, pop-up hints can be displayed when the mouse cursor hovers over the label. You can either display text from the _[Hint](TPJHotLabelHint.md)_ property as normal, display the _[URL](TPJHotLabelURL.md)_ property value (useful when the URL is not displayed in the label) or customise the hint each time it is displayed. The _[HintStyle](TPJHotLabelHintStyle.md)_ property is used to specify the source of the hint text. Custom hints are set up by handling the _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ event.

## Methods ##

_TPJHotLabel_ defines no new methods over and above those inherited from _TLabel_.

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[Caption](TPJHotLabelCaption.md)_ | Specifies a text string that that may be displayed in the label. How _[Caption](TPJHotLabelCaption.md)_ is used depends on the _[CaptionIsURL](TPJHotLabelCaptionIsURL.md)_ property. |
| _[CaptionIsURL](TPJHotLabelCaptionIsURL.md)_ | Determine whether the text of the label's _[URL](TPJHotLabelURL.md)_ property is assigned to the _[Caption](TPJHotLabelCaption.md)_ property or whether _[Caption](TPJHotLabelCaption.md)_ can be used to display descriptive text. |
| _[Cursor](TPJHotLabelCursor.md)_ | Specifies the image used to represent the mouse pointer when it passes into the region covered by the control. |
| _[Font](TPJHotLabelFont.md)_ | Specifies the label's font when in its normal state, i.e. when it is neither highlighted or in its visited state. |
| _[HighlightFont](TPJHotLabelHighlightFont.md)_ | Specifies the label's font when in its highlighted state. |
| _[HighlightURL](TPJHotLabelHighlightURL.md)_ | Determines whether the label's text is highlighted when the mouse passes over the control. |
| _[Hint](TPJHotLabelHint.md)_ | Contains the text string that can appear when the user moves the mouse over the control. How _[Hint](TPJHotLabelHint.md)_ is used depends on the _[HintStyle](TPJHotLabelHintStyle.md)_ property. |
| _[HintStyle](TPJHotLabelHintStyle.md)_ | Determines the source of the text displayed in the component's hint. |
| _[ParentFont](TPJHotLabelParentFont.md)_ | Determines where the control looks for its font information. |
| _[TrackVisits](TPJHotLabelTrackVisits.md)_<sup>[v2.2]</sup> | Determines whether or not the label automatically displays in its visible state when the user clicks the link. |
| _[URL](TPJHotLabelURL.md)_ | Stores the URL that is to be accessed when the label is clicked. |
| _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> | Determines whether or not the label is in its visited state. |
| _[VisitedFont](TPJHotLabelVisitedFont.md)_<sup>[v2.2]</sup> | Specifies the label's font when in its visited state and not highlighted. |
| _[ValidateURL](TPJHotLabelValidateURL.md)_ | Determines whether the URL stored in the component is validated or not. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ | An event that enables the user to specify a custom hint to be displayed by the component. |