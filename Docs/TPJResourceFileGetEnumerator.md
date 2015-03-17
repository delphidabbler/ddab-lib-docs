# GetEnumerator method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

**Introduced:** v1.1

```pascal
function GetEnumerator: TPJResourceFileEnumerator;
```

Creates and returns a new enumerator of type _[TPJResourceFileEnumerator](TPJResourceFileEnumerator.md)_**<sup>v1.1</sup>** that can enumerate the resources contained in a _[TPJResourceFile](TPJResourceFile.md)_ instance.

The purpose of _GetEnumerator_ is to enable a _[TPJResourceFile](TPJResourceFile.md)_ instance to be enumerated in a **for..in** loop construct. In such cases _GetEnumerator_ is called automatically and there is rarely any need call the method from code.

On compilers that don't support **for..in** loops (i.e. Delphi 7 and earlier) you can call _GetEnumerator_ from code to get an enumerator instance and use that to perform the enumeration (usually using a **while** loop). Once the enumeration is complete you must free the enumerator object. However, it is usually simpler to use the traditional **for..do** loop to iterate over the indexes of the available entries.

**Example 1:**

Here is how to iterate the resource entries in Delphi 2005 and later.

Assume there is a _[TPJResourceFile](TPJResourceFile.md)_ instance named _ResFile_ and a method _DoSomething_ that takes a _[TPJResourceEntry](TPJResourceEntry.md)_ parameter.

```pascal
var
  Entry: TPJResourceEntry;
  ...
begin
  ...
  for Entry in ResFile do
    DoSomething(Entry);
  ...
end;
```

Notice that neither _GetEnumerator_ nor the methods of _[TPJResourceFileEnumerator](TPJResourceFileEnumerator.md)_**<sup>v1.1</sup>** are called explicitly.

**Example 2:**

This example shows how to use the enumerator from code, as must be done when using Delphi 7 and earlier.

Assumes the _ResFile_ object and the _DoSomething_ method used in Example 1 are available.

```pascal
var
  Enum: TPJResourceFileEnumerator;
begin
  ...
  Enum := ResFile.GetEnumerator;
  try
    while Enum.MoveNext do
      DoSomething(Enum.Current);
  finally
    Enum.Free;
  end;
end;  
```