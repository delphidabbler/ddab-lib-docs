#summary Resource File Unit Example 5.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Example #5: Adding to or modifying a resource's data =

While the code in the [ResFileUnit Resource File Unit] does not understand the various resource data formats it does assist in reading, adding, updating and deleting the raw resource data.

The following properties and methods of _[TPJResourceEntry]_ are useful in reading, adding, updating and deleting the raw data:

  * The _[TPJResourceEntry#Properties Data]_ property. This exposes the resource data as a _TStream_ which means that we can use normal stream handling techniques to read and modify the data.
  * The _[TPJResourceEntry#Properties DataBytes]_*^v1.1^* property makes the resource data available as a byte array.
  * The _[TPJResourceEntryClearData ClearData]_*^v1.1^* method deletes the resource data.

In the following section we show how manipulate data using these properties and method.

== Reading data ==

The following code fragment shows how to read all the data from a resource entry to a buffer using the _[TPJResourceEntry#Properties Data]_ property.

{{{
var
  Entry: TPJResourceEntry;
  Buf: PByte;
begin
  ...
  // Make sure Entry references a resource object
  ...
  // Create buffer of required size
  GetMem(Buf, Entry.DataSize);
  try
    // Make sure resource data stream at start
    Entry.Data.Position := 0;
    // Read all resource data into buffer
    Entry.Data.ReadBuffer(Buf^, Entry.DataSize);
    // Rewind data stream again
    Entry.Data.Position := 0;
    ...
    // Do something with Buf
    ...
  finally
    // Release buffer
    FreeMem(Buf);
  end;
end;
}}}

We first set the buffer to the required size by getting the size of the resource from the _[TPJResourceEntry]_'s _[TPJResourceEntry#Properties DataSize]_ property (you could also use the _[TPJResourceEntry#Properties Data].Size_ property). We now ensure the resource data stream is positioned at the start (you can't assume this!) then read all the data into the buffer using _TStream_'s _!ReadBuffer_ method. We then reposition the stream ready for the next use. Having processed the data in the buffer in some way we finally free it.

It may be more convenient to copy the resource data to another stream before processing it. The next example illustrates this by storing the resource data in a file named `ResEntry.dat`:

{{{
var
  Entry: TPJResourceEntry;
  FS: TFileStream;
begin
  ...
  // Make sure Entry references a resource object
  ...
  // Open stream onto new file
  FS := TFileStream.Create('ResEntry.dat', fmCreate);
  try
    // Copy resource data to file
    FS.CopyFrom(Entry.Data, 0);
    Entry.Data.Position := 0;
  finally
    // Close the file
    FS.Free;
  end;
end;
}}}

Here we first open a stream onto a new file. We then use _TStream_'s _!CopyFrom_ method to copy the whole of the resource data to the file stream. By specifying a size of `0` in the _!CopyFrom_ method, _TStream_ automatically positions the resource data stream at the start and copies the whole stream, so we don't need to position it first. Once again we reset the resource data stream once we are done.

Depending on how you want to manipulate the resource data it may be much simpler to use the _[TPJResourceEntry#Properties DataBytes]_*^v1.1^* property to get an array of bytes to manipulate. Here's an example that is so simple it is hardly worth giving:

{{{
var
  Entry: TPJResourceEntry;
  Bytes: TBytes;
begin
  ...
  // Make sure Entry references a resource object
  ...
  Bytes := Entry.DataBytes;
  ...
  // Do something with Bytes
end;
}}}

== Deleting data ==

The simplest way to delete the data is to call the _[TPJResourceEntry]_._[TPJResourceEntryClearData ClearData]_*^v1.1^* method:

{{{
var
  Entry: TPJResourceEntry;
begin
  // Make sure Entry references a resource object
  ...
  Entry.ClearData;
  ...
end;
}}}

In v1.0 of the Resource File Unit there is no direct way to clear the data. It is still very easy to do though. Simply set the data stream's size to `0`:

{{{
var
  Entry: TPJResourceEntry;
begin
  ...
  // Make sure Entry references a resource object
  ...
  Entry.Data.Size := 0;
  ...
end;
}}}

*Note:* You must set the _Size_ property of the entry's _[TPJResourceEntry#Properties Data]_ property here: you can't set the _[TPJResourceEntry#Properties DataSize]_ property since it is read only.

== Writing data ==

We can add data to an existing resource quite simply. Let us first look at how to overwrite any existing data and then show how to append data to an existing resource. For the purposes of this example, assume we have a user defined resource that stores some plain text. _Entry_ is a _[TPJResourceEntry]_ object that references our resource. We will replace any existing data with the text `'Hello World'`.

First of all we use the _[TPJResourceEntry#Properties Data]_ property:

{{{
var
  Entry: TPJResourceEntry;
  Text: string;
begin
  ...
  // Make sure Entry references a resource object
  ...
  // Delete any existing data
  Entry.Data.Size := 0;  // in v1.1 use Entry.ClearData instead
  // Write the required text
  Text := 'Hello World';
  Entry.Data.WriteBuffer(Pointer(Text)^, Length(Text) * SizeOf(Char));
  // Position data ready for reading
  Entry.Data.Position := 0;
  ...
end;
}}}

That's well and good when you want to write the text in its native encoding. When you want to write the text in another encoding, say UTF-8, that is when the _[TPJResourceEntry#Properties DataBytes]_*^v1.1^* property really helps. Assuming you are using Delphi 2009 or later you can replace any existing data with the text `'Hello World'`, using UTF-8, like this:

{{{
var
  Entry: TPJResourceEntry;
begin
  ...
  // Make sure Entry references a resource object
  ...
  Entry.DataBytes := TEncoding.UTF8.GetBytes('Hello World');
  ...
end;
}}}

Now let's look at how we add more text to the end of the resource data using the _[TPJResourceEntry#Properties Data]_ property. We will appended the text `'www.delphidabbler.com'` to the end of some existing text in the resource:

{{{
var
  Entry: TPJResourceEntry;
  Text: string;
begin
  ...
  // Make sure Entry references a resource object
  ...
  // Move to end of existing data
  Entry.Data.Seek(0, soFromEnd);
  // Write new text
  Text := 'www.delphidabbler.com';
  Entry.Data.WriteBuffer(Pointer(Text)^, Length(Text) * SizeOf(Char));
  // Reposition stream to start
  Entry.Data.Position := 0;
  ...
end;
}}}

Here we move the stream pointer to the end of the stream so the text we write is appended to any existing data.

A similar thing using can be done using the _[TPJResourceEntry#Properties DataBytes]_*^v1.1^* property. Assume the existing text is in UTF-8 and were want to append text in the same format. To do this we have to read the existing text, append the new text and then write the whole string back again, as follows:

{{{
var
  Entry: TPJResourceEntry;
  Text: string;
begin
  ...
  // Make sure Entry references a resource object
  ...
  Text := TEncoding.UTF8.GetString(Entry.DataBytes)
    + #13#10'www.delphidabbler.com';
  Entry.DataBytes := TEncoding.UTF8.GetBytes(Text);
  ...
end;
}}}

Finally, you can add data to a resource's data by loading it directly from file using the _[TPJResourceEntryLoadDataFromFile LoadDataFromFile]_*^v1.1^* method. This method can either replace a resource's current data with the content of a file or append the content of the file to the current data.

Here's an example:

{{{
var
  Entry: TPJResourceEntry;
begin
  ...
  // Make sure Entry references a resource object
  ...
  // Replace any existing resource data with content of file Foo.dat
  Entry.LoadDataFromFile('Foo.dat', False);
  // Append content of file Bar.dat to resource data
  Entry.LoadDataFromFile('Bar.dat', True);
  ...
end;
}}}

Suppose `Foo.dat` contained the ASCII string `'forty-two'` and `Bar.dat`
contained the ASCII string `'fifty-six'` then after running the above code then
the resource data would contain bytes that, when converted to an ASCII string,
would read `forty-twofifty-six`.

*Links:*

  * [ResFileExample6 Next Example]
  * [ResFileExample4 Previous Example]
  * Back to [ResFileExamples List of Examples]