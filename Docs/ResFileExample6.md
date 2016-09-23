# Example #6: Adding a new resources to a file #

We can add new resources to an existing file using _[TPJResourceFile](TPJResourceFile.md)_'s _[AddEntry](TPJResourceFileAddEntry.md)_ method. Each new resource must be uniquely named within the resource file (i.e. its combined resource type, name and language id must be unique), otherwise an exception will be raised.

There are two versions of _[AddEntry](TPJResourceFileAddEntry.md)_. The first simply adds a new empty resource with zeroed header properties while the second version adds a renamed copy of an existing resource. Both versions of _[AddEntry](TPJResourceFileAddEntry.md)_ take an optional language identifier. If this is not specified then the resource is language neutral (_LanguageID_ = `0`).

The following code snippet adds four new resource entries to an existing resource file object:

  1. An empty, language neutral, `RCDATA` resource with ordinal name `42`. The entry's _MemoryFlags_ property is then set to "Discardable" and its data is set to `'Hello World'`.
  1. A new language neutral `RCDATA` resource that is a copy of the first entry but named `'FORTYTWO'`. This resource has the same _MemoryFlags_ and _Data_ as the first entry.
  1. A new `RCDATA` resource also named `'FORTYTWO'` but with a language id of `$0809`. Again this resource is a copy of the first one.
  1. A new empty `RCDATA` resource named `42` with language id of `$0809`.

```pascal
var
  ResFile: TPJResourceFile;
  Entry1, Entry2, Entry3, Entry4: TPJResourceEntry;
const
  s42 = 'FORTYTWO';
  ord42 = MakeIntResource(42);
  sHello = 'Hello World';
begin
  ...
  // Assume ResFile references a valid object

  // Create 1st entry: empty
  Entry1 := fResFile.AddEntry(RT_RCDATA, ord42);
  // now set mem flags and data
  Entry1.MemoryFlags := RES_MF_DISCARDABLE;
  Entry1.Data.WriteBuffer(Pointer(sHello)^, Length(sHello) * SizeOf(Char));
  Entry1.Data.Position := 0;

  // Create 2nd entry as copy of entry 1
  Entry2 := fResFile.AddEntry(Entry1, s42);

  // Create 3rd entry as copy of entry 1 with language id of $0809
  Entry3 := fResFile.AddEntry(Entry1, s42, $0809);

  // Create 4th entry: empty with language id of $0809
  Entry4 := fResFile.AddEntry(RT_RCDATA, ord42, $0809);

  // Do something with the entries
  ...
end;
```

The entries we have created have the following properties:

| | **Entry 1** | **Entry 2** | **Entry 3** | **Entry 4** |
|:------------|:------------|:------------|:------------|:------------|
| **Type** | `RT_RCDATA` | `RT_RCDATA` | `RT_RCDATA` | `RT_RCDATA` |
| **Name** | `42` | `'FORTYTWO'` | `'FORTYTWO'` | `42` |
| **LanguageID** | `0` | `0` | `$0809` | `$0809` |
| **MemoryFlags** | `$0100` | `$0100` | `$0100` | `0` |
| **Data** | `'Hello World'` | `'Hello World'` | `'Hello World'` |  |

**Links:**

  * [Next Example](ResFileExample7.md)
  * [Previous Example](ResFileExample5.md)
  * Back to [List of Examples](ResFileExamples.md)
