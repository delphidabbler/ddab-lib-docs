# Examples: Using Highlighting #

These examples present two possible designs for _[TPJHotLabel](TPJHotLabel.md)_ components that use text highlighting to indicate that the label is clickable.

## Example 1 ##

This example uses a change in text decoration to highlight the text of the label when the mouse passes over it.

First we must enable highlighting by setting _[HighlightURL](TPJHotLabelHighlightURL.md)_ to `True`. Then we set _[Font](TPJHotLabelFont.md).Style_ to `[]`, _[HighlightFont](TPJHotLabelHighlightFont.md).Style_ to `[fsUnderline]` and make _[HighlightFont](TPJHotLabelHighlightFont.md).Color_ the same as _[Font](TPJHotLabelFont.md).Color_. We use a colour that is different from the standard label font to indicate the label is clickable.

Start a new application and place a _[TPJHotLabel](TPJHotLabel.md)_ component on the form. Now select the component and use the object inspector to set the following property values:

| **Property** | **Value** |
|:-------------|:----------|
| Font.Color | `clBlue` |
| Font.Style | `[]` |
| HighlightFont.Color | `clBlue` |
| HighlightFont.Style | `[fsUnderline]` |
| HighlightURL | `True` |

If you don't want to use the object inspector you can double click the form to create a _FormCreate_ event handler and enter the following code in it, which assumes the component is named _PJHotLabel1_:

```pascal
PJHotLabel1.Font.Color := clBlue;
PJHotLabel1.HighlightFont.Color := PJHotLabel1.Font.Color;
PJHotLabel1.Font.Style := [];
PJHotLabel1.HighlightFont.Style := [fsUnderline];
PJHotLabel1.HighlightURL := True;
```

Now compile and run the application and roll the mouse over the URL and see the highlighting. The un-highlighted label will display with no text decoration and it will become underlined when the mouse passes over it.

## Example 2 ##

The second example uses component's default highlighting style where un-highlighted text is navy blue and underlined and highlighted text is red and also underlined.

Start a new application and drop a _[TPJHotLabel](TPJHotLabel.md)_ component on the form. We only need to set the _[HighlightURL](TPJHotLabelHighlightURL.md)_ property to `True`, leaving all the other properties unchanged. You can use the property inspector do this or create a _FormCreate_ event handler and enter the following line of code, assuming the component is named _PJHotLabel1_:

```pascal
PJHotLabel1.HighlightURL := True;
```

Again, run the application and move the mouse cursor over the control to see the highlighting effect.

**Link:**

  * Back to [Hot Label Component Page](HotLabelComponent.md)