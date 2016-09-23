# Resource File Helper Routines #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

These helper routines are to assist in manipulating resource identifiers. They can be useful when working with Windows API routines as well as the classes provided in this unit. They are:

  * [IsIntResource](#isintresource)
  * [IsEqualResID](#isequalresid)
  * [ResIDToStr](#residtostr)

## IsIntResource ##

```pascal
function IsIntResource(const ResID: PChar): Boolean;
```

This is a clone of the `IS_INTRESOURCE` macro defined on MSDN that checks if a resource identifier is ordinal or a string. Complements the _MakeIntResource_ "macro" defined in _Windows.pas_.

**_Parameter:_**

  * _ResID_: The resource identifier to be checked. May be either an numeric identifier (like those produced by _MakeIntResource_, or a name in the form of a null terminated string.

**_Returns:_**

  * `True` if _ResID_ is numeric or `False` if it is a null terminated string.

## IsEqualResID ##

```pascal
function IsEqualResID(const R1, R2: PChar): Boolean;
```

Checks for equality of two resource identifiers. To be equal the identifiers either be ordinal and have the same value or must both point to strings that have the same text when case is ignored.

**_Parameters:_**

  * _R1_: The first resource identifier to check.
  * _R2_: The second resource identifier to check.

**_Returns:_**

  * `True` if the identifiers are equal and `False` otherwise.

## ResIDToStr ##

```pascal
function ResIDToStr(const ResID: PChar): string;
```

Converts a resource identifier into its string representation as defined on MSDN.

**_Parameter:_**

  * _ResID_: The resource identifier to convert.

**_Returns:_**

  * The required string representation. If the identifier is a string pointer then the string itself is returned. If the identifier is ordinal then the returned string is the integer value preceded by a # character.
