# EOLMarker property

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
property EOLMarker: AnsiString;
```

## Description

This property specifies the ANSI character or characters that mark the end of a line of ANSI text.

The filter splits lines of text read from the associated pipe based on the value of the property. The [_OnLineEnd_](./TPJAnsiSBCSPipeFilter-OnLineEnd.md) event is triggered for each line read.

The property defaults to #13#10.

## Remarks

It is usual to use the default property value or #10 or #13 on their own, but any string of ANSI text can be used.
