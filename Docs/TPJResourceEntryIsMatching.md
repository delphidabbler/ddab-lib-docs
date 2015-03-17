# IsMatching methods #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceEntry](TPJResourceEntry.md)_

There are two overloaded _IsMatching_ methods. They are both used to check if a resource matches the one represented by the _[TPJResourceEntry](TPJResourceEntry.md)_ object on which the method is called.

Matching involves comparing the resource entries' names, types and language ids. In the first version of the method comparison of names and / or types can be omitted.


---


```pascal
function IsMatching(const ResType, ResName: Pchar;
  const LangID: Word = $FFFF): Boolean;
```

Checks if the resource entry has the given type, name and language id. The resource name and/or language id can be ignored in which case only the values provided will be matched. For example to match only a resource type use `IsMatching(MyResType, nil);`.

**_Parameters:_**

  * _ResType_: The type of the resource to be matched as either an ordinal or string type.
  * _ResName_: The name of the resource to be matched as either an ordinal or string type. If `nil` is passed as this parameter then it is ignored when matching.
  * _LangID_: The language id of the resource to be matched. If this parameter is left out or if `$FFFF` is passed then the language id is ignored in the match. To test for a language neutral resource specify `0` here.

**_Returns:_**

`True` if the resources match or `False` if they do not.


---


```pascal
function IsMatching(const Entry: TPJResourceEntry): Boolean;
```

Checks if the resource entry has the same type, name and language id as another resource entry.

**_Parameter:_**

  * _Entry_: The resource entry object to match against.

**_Returns:_**

`True` if the entries type, name and language id are all the same or `False` if they are not.