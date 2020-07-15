# [Console Application Runner Classes](../../ConsoleApp.md) Example 11: Customising the appearance of the console

[_TPJConsoleApp_](../API/TPJConsoleApp.md) can be used to customise the appearance of any new console window displayed by a console application. This example shows how to modify the console window's size, position, title and foreground and background colours.

> Console customisation requires a _new_ console window. If one console application starts another and the child application shares the parent's console then any customisation will have no effect. However, if the parent program is a GUI application then a new console window is always created.

To avoid too much complexity all in one go we will develop this example project in four stages, with each stage demonstrating one property of [_TPJConsoleApp_](../API/TPJConsoleApp.md):

1. [_ConsoleTitle_](../API/TPJCustomConsoleApp-ConsoleTitle.md)
2. [_ConsoleColors_](../API/TPJCustomConsoleApp-ConsoleColors.md)
3. [_WindowSize_](../API/TPJCustomConsoleApp-WindowSize.md)
4. [_WindowPosition_](../API/TPJCustomConsoleApp-WindowPosition.md)

Before that we'll create the main example program framework that is required to demonstrate all the properties.

## Common Code

To begin with start a new Delphi GUI application project, and add [_PJConsoleApp_](../API/PJConsoleApp.md) to the the main form's uses statement.

Now drop a _TButton_ on the form, name it `btnRun` and give it the following _OnClick_ event handler:

```pascal
procedure TForm1.btnRunClick(Sender: TObject);
var
  App: TPJConsoleApp;
begin
  btnRun.Enabled := False;
  try
    App := TPJConsoleApp.Create;
    try
      // [ConsoleTitle code here]
      // [ConsoleColor code here]
      // [WindowSize code here]
      // [WindowPosition code here]
      App.OnWork := WorkHandler;
      App.Visible := True;
      if not App.Execute('Timed 2') then
        raise Exception.CreateFmt(
          'Can_t execute program: error %d - "%s"',
          [App.ErrorCode, App.ErrorMessage]
        );
    finally
      App.Free;
    end;
  finally
    btnRun.Enabled := True;
  end;
end;
```

If you've worked through other examples, none of the above should come as any surprise. Note that we've explicitly made the console application visible so we can see the customisations! The code we add in the following sections will replace the relevant placeholder comments in the above code.

Now add the following method to handle the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event. It's the same simple implementation we've used before that allows the GUI to remain responsive:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
begin
  Application.ProcessMessages;
end;
```

You can now test the application. Clicking the button will run the console app without any customisations.

> Once again we've use `Timed.exe` as the console app and run it for 2 seconds, which should be long enough to notice the customisations. If it's not then change the program's parameter to increase the number of seconds it runs. You can substitute any console application that runs for a sufficient length of time.

## Stage 1: ConsoleTitle

Add a _TEdit_ to the form and name it `edTitle`. It would be useful for clarity to also add a _TLabel_ to label the edit control as "Title".

In the _btnRunClick_ event handler replace the `[ConsoleTitle code here]` placeholder comment with:

```pascal
App.ConsoleTitle := edTitle.Text;
```

Now run the program, type a title in the edit box and click the button. The console window should have the title you entered. Setting the title to an empty string causes the default window title to be displayed.

## Stage 2: ConsoleColors

Drop a _TGroupBox_ on the form. Inside the group box add two _TColorBox_ controls, one named `cbForeground` and the other `cbBackground`. It may be helpful to label the colour combos "Foreground" and "Background" respectively with _TLabel_ components.

The colour combo boxes will be used to select the background and foreground colours of the console. The possible colours are restricted to the 16 basic system colours. So set the _Style_ property of both combos to `[cbStandardColors]`. You can also include `cbPrettyNames` if you want proper colour names.

Now replace the placeholder comment in _btnRunClick_ with this code:

```pascal
App.ConsoleColors := MakeConsoleColors(
  cbForeground.Selected, cbBackground.Selected
);
```

This assigns the required colours to the [_ConsoleColors_](../API/TPJCustomConsoleApp-ConsoleColors.md) property. Note that we can't assign the fields of the property separately, because they are read-only. So we must assign a whole [_TPJConsoleColors_](../API/TPJConsoleColors.md) record to the property. To do this we take advantage of the [_MakeConsoleColors_](../API/Routines.md#makeconsolecolors) routine to construct the required [_TPJConsoleColors_](../API/TPJConsoleColors.md) record.

> There are two overloaded versions of [_MakeConsoleColors_](../API/Routines.md#makeconsolecolors). The first takes [_TPJConsoleColor_](../API/TPJConsoleColor.md) parameters and the second takes _TColor_ parameters. We've used the second version to avoid the hassle of converting the _TColor_ values read from the combo boxes to the [_TPJConsoleColor_](../API/TPJConsoleColor.md) values needed by the [_TPJConsoleColors_](../API/TPJConsoleColors.md) record. The routine does the conversion for us.

Rebuild and run the GUI application. Select some colours and click the _Run_ button. Notice the colours are used in the console window.

## Stage 3: WindowSize

Drop another _TGroupBox_ on the form. In the group box add a _TCheckBox_ named `cbDefWindowSize` with caption `'Use default'` along with two _TEdit_s, named `edWindowWidth` and `edWindowHeight`. Label the edit controls "Width" and "Height" using _TLabel_ components.

Select both edit controls and add the same _OnKeyPress_ event handler, named _EdNumberFilter_, to both of them. Code the event handler as follows:

```pascal
procedure TForm1.EdNumberFilter(Sender: TObject; var Key: Char);
begin
  {$IFDEF UNICODE}
  if not CharInSet(Key, ['0'..'9', #8]) then
  {$ELSE}
  if not (Key in ['0'..'9', #8]) then
  {$ENDIF}
    Key := #0;
end;
```

> We will use the same event handler again later.

This event handler ensures that only digits can be entered in the edit controls because we use them to specify the width and height of the console window in pixels. (The `#8` character represents a backspace character and is there to allow the backspace key to work.)

Finally, replace the placeholder commment in _btnRunClick_ with this code:

```pascal
if not cbDefWindowSize.Checked then
  App.WindowSize := MakeSize(
    StrToInt(edWindowWidth.Text), StrToInt(edWindowHeight.Text)
  );
```

This simply sets the [_WindowSize_](../API/TPJCustomConsoleApp-WindowSize.md) property to the width and height entered in the edit controls providing the check box is not checked. When the check box is checked no property value is set and its default value is used.

Here we have used the [_MakeSize_](../API/Routines.md#makesize) helper routine that constructs a _TSize_ record, setting its fields to the value of the two parameters. This is helpful since it is not possible to assign the fields of the [_WindowSize_](../API/TPJCustomConsoleApp-WindowSize.md) property individually; we must assign a complete record to the property.

Rebuild and run the application. Make sure the _Use default_ check box is cleared and enter some sensible values for width and height (say 640 by 480) in the edit controls. Click the _Run_ button. Notice the size of the window. Now repeat with the check box ticked. The values in the edit controls will be ignored and the console will have its default size.

> Entering zero in either the width or height edit controls will cause the size to be ignored and the default console size to be used.

## Stage 4: WindowPosition

The code to demonstrate [_WindowPosition_](../API/TPJCustomConsoleApp-WindowPosition.md) is very similar to that for [_WindowSize_](../API/TPJCustomConsoleApp-WindowSize.md). You again need a _TGroupBox_ containing two _TEdit_ controls and a _TCheckbox_. The check box caption should again be `'Use default'` but name it `cbDefWindowPos`. Name the edit controls `edWindowLeft` and `edWindowTop`. Use _TLabel_ components to label the edit controls "Left" and "Top".

Connect both edit controls' _OnKeyPress_ events to the same _EdNumberFilter_ event handler shown above.

Replace the placeholder commment in _btnRunClick_ with this code:

```pascal
if not cbDefWindowPos.Checked then
  App.WindowPosition := Point(
    StrToInt(edWindowLeft.Text), StrToInt(edWindowTop.Text)
  );
```

This works pretty much the same as the similar code in stage 3 above. The main difference being that, because [_WindowPosition_](../API/TPJCustomConsoleApp-WindowPosition.md) has type _TPoint_, we construct the record value assigned to the property using the _Point_ function from the Delphi VCL.

Rebuild the application one last time and run it. Clear the checkbox and enter values for the console window's top left corner in screen co-ordinates. Click the _Run_ button and observe the position of the console window. Run again and note that the window appears in the same position. Now tick the checkbox and run again. The console window appears in a default position. Run a few more times and you'll notice the window's default position moves each time.

## Links

* [Next example](./Example12.md)
* [Previous example](./Example10.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
