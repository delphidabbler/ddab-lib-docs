# Example: Tracking visits to URLs.<sup>[v2.2]</sup> #

The component provides the _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> property to enable visits to the URLs associated with hot label components to be tracked. Furthermore, the _[TrackVisits](TPJHotLabelTrackVisits.md)_<sup>[v2.2]</sup> property enables the tracking to be done automatically whenever the label is clicked and the underlying action completes successfully.

So, assuming we have a number of _[TPJHotLabel](TPJHotLabel.md)_ components on a form, each of which has the _[URL](TPJHotLabelURL.md)_ property set to some valid URL and their _[TrackVisits](TPJHotLabelTrackVisits.md)_<sup>[v2.2]</sup> property set to `True` then simply by running the application and clicking a few links we will see that each label changes colour when visited.

However when the application is restarted we find that the tracking information is lost and all labels are reset to their un-visited state. This behaviour is to be epected because the _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> does not maintain state.

In this example we will implement a scheme that persists the visited state of the hot label controls between executions.

Start a new VCL forms application and drop a few _[TPJHotLabel](TPJHotLabel.md)_ components on the form. Give each component's _[URL](TPJHotLabelURL.md)_ property a valid value and set all the component's _[TrackVisits](TPJHotLabelTrackVisits.md)_<sup>[v2.2]</sup> properties to `True`.

In this example we will use an ini file to persist the visited state of the hot label controls and we will use the hot label component's _Name_ property to uniquely identify the individual controls. If there is no ini file present we will assume that no hot labels have been visited.

We will write the ini file when the form is destroyed, so create an _OnDestroy_ event handler for the form and implement it as follows:

```pascal
procedure TForm1.FormDestroy(Sender: TObject);
var
  Ini: TIniFile;
  I: Integer;
begin
  Ini := TIniFile.Create(IniFileName);
  try
    for I := 0 to Pred(ComponentCount) do
    begin
      if Components[I] is TPJHotLabel then
        Ini.WriteBool(
          'Visited', Components[I].Name, (Components[I] as TPJHotLabel).Visited
        );
    end;
  finally
    Ini.Free;
  end;
end;
```

This simply creates an ini file with the name given by _IniFileName_ (which we'll come back to) then loops across all components on the form and, whenever a _[TPJHotLabel](TPJHotLabel.md)_ is found, writes its name and the value of its _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> property to the ini file.

Having recorded the information all we need to do is to read it in when the program starts and set the visited state of the required hot label components. We do this in the form's _OnCreate_ handler:

```pascal
var
  Ini: TIniFile;
  I: Integer;
  HotLbl: TPJHotLabel;
begin
  Ini := TIniFile.Create(IniFileName);
  try
    for I := 0 to Pred(ComponentCount) do
    begin
      if Components[I] is TPJHotLabel then
      begin
        HotLbl := Components[I] as TPJHotLabel;
        HotLbl.Visited := Ini.ReadBool('Visited', HotLbl.Name, False);
      end;
    end;
  finally
    Ini.Free;
  end;
end;
```

This code is the inverse of the code we used to write the file. It loops through every component as before, looking for hot label components. When it finds one it tries to read a value from the ini file that matches the component's name. If it finds the required value the component's _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> property is set to the value read from the ini file. If the component's name is not in the ini file then its _[Visited](TPJHotLabelVisited.md)_<sup>[v2.2]</sup> property is set to `False`. Note that this code works even if there is no ini file.

That just leaves _IniFileName_. You can implement this as a function or method that returns the required file name. For example, you could store the file in the same directory as the executable by implementing _IniFileName_ as a private form method follows:

```pascal
function TForm1.IniFileName: string;
begin
  Result := ExtractFilePath(ParamStr(0)) + 'hotlabel.ini';
end;
```

This is not recommended for programs that are installed in the "Program Files" directory, but it's OK for portable apps and test code.

That's all the code you need. Run the program, click one or more labels so that they change their state then close the program. Re-run it and you should find that the visited state of the hot labels has been preserved.

**Remarks**

Although the code can handle hot label components being deleted or new ones being added it falls down if a component is renamed or a new component has the same name as one that has been deleted. A more involved system of choosing unique keys associated with each control will be needed to work round this, possibly using the _Tag_ property to store a value unique to each component.

You should note that the concept of visiting URLs in hot label components differs from that which is used in browsers. In a browser it is the URL that is flagged as visited: if a URL has been visited then all links that reference the URL are rendered as visited. With hot label components this is not the case: it is the component that stores the visited state, not the URL. Therefore if more than one component has the same URL, visiting one does not flag the others as visited.

**Link:**

  * Back to [Hot Label Component Page](HotLabelComponent.md)