#summary Description of the TPJResourceFile.GetEnumerator method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !GetEnumerator method =

*Project:* [ResFileUnit Resource File Unit]

*Unit:* _PJResFile_.

*Class:* _[TPJResourceFile TPJResourceFile]_

*Introduced:* v1.1

{{{
function GetEnumerator: TPJResourceFileEnumerator;
}}}

Creates and returns a new enumerator of type _[TPJResourceFileEnumerator]_*^v1.1^* that can enumerate the resources contained in a _[TPJResourceFile]_ instance.

The purpose of _!GetEnumerator_ is to enable a _[TPJResourceFile]_ instance to be enumerated in a *for..in* loop construct. In such cases _!GetEnumerator_ is called automatically and there is rarely any need call the method from code.

On compilers that don't support *for..in* loops (i.e. Delphi 7 and earlier) you can call _!GetEnumerator_ from code to get an enumerator instance and use that to perform the enumeration (usually using a *while* loop). Once the enumeration is complete you must free the enumerator object. However, it is usually simpler to use the traditional *for..do* loop to iterate over the indexes of the available entries.

*Example 1:*

Here is how to iterate the resource entries in Delphi 2005 and later. 

Assume there is a _[TPJResourceFile]_ instance named _!ResFile_ and a method _!DoSomething_ that takes a _[TPJResourceEntry]_ parameter.

{{{
var
  Entry: TPJResourceEntry;
  ...
begin
  ...
  for Entry in ResFile do
    DoSomething(Entry);
  ...
end;
}}}

Notice that neither _!GetEnumerator_ nor the methods of _[TPJResourceFileEnumerator]_*^v1.1^* are called explicitly.

*Example 2:*

This example shows how to use the enumerator from code, as must be done when using Delphi 7 and earlier.

Assumes the _!ResFile_ object and the _!DoSomething_ method used in Example 1 are available.

{{{
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
}}}