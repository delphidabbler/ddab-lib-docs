# EOLMarker property

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md)

```pascal
property EOLMarker: UnicodeString;
```

## Description

This property specifies the Unicode character or characters that mark the end of a line of Unicode text.

The filter splits lines of text read from the associated pipe based on the value of the property. The [_OnLineEnd_](./TPJUnicodeBMPPipeFilter-OnLineEnd.md) event is triggered for each line read.

The property defaults to #13#10.

## Remarks

It is usual to use the default property value or #10 or #13 on their own, but any string of Unicode text can be used.

Note that the _UnicodeString_ type must be defined to use this property. This is a native type on Delphi 2009 or later. For Delphi 2007 and earlier the [_PJPipeFilters_](./PJPipeFilters.md) unit defines _UnicodeString_ as _WideString_.
