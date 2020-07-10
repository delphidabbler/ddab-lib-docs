# DoFilter abstract method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Class:*** [_TPJPipeFilter_](./TPJPipeFilter.md)

```pascal
procedure DoFilter(const ValidData: TBytes); virtual; abstract;
```

## Description

Performs the filtering operation on given data. The action to be performed depends on the purpose of the filter. Descendant classes must override this method to perform the required filtering.

Data to be filtered is passed in the _ValidData_ parameter. This byte array is guaranteed to contain only valid, processable data. Any "carry forward" bytes will have been trimmed from the array before passing to this method by trimming off the number of bytes returned from the [_LeftOverByteCount_](./TPJPipeFilter-LeftOverByteCount.md) method.

## Example

Both [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) and [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) first convert the bytes of _ValidData_ into text (Unicode in the former case and ANSI text in the latter).

They then trigger their respective _OnText_ events to report the text that has just been read. Following that they parse the text into lines and trigger their _OnLineEnd_ event for each line parsed. Any partial lines are carried forward until the next time the method is called.

Here is [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)'s implementation of the method:

```pascal
procedure TPJAnsiSBCSPipeFilter.DoFilter(const ValidData: TBytes);
var
  Text: AnsiString;  // Text read from ValidData
  EOLPos: Integer;   // Position(s) of end of line marker in text
begin
  // NOTE: code assumes SizeOf(AnsiChar) = 1
  // Record ANSI SBCS text
  SetLength(Text, Length(ValidData));
  Move(Pointer(ValidData)^, Pointer(Text)^, Length(ValidData));
  // Trigger OnText event for read text
  DoText(Text);
  fPartialLine := fPartialLine + Text;
  // Break text into lines separated by EOLMarker, trigger OnLineEnd for each
  EOLPos := Pos(fEOLMarker, fPartialLine);
  while EOLPos > 0 do
  begin
    DoLineEnd(Copy(fPartialLine, 1, EOLPos - 1));
    fPartialLine := Copy(
      fPartialLine, EOLPos + Length(fEOLMarker), MaxInt
    );
    EOLPos := Pos(fEOLMarker, fPartialLine);
  end;
end;
```

_fPartialLine_ stores text that is yet to be reported via the _OnLineEnd_ event, _DoLineEnd_ triggers the _OnLineEnd_ event and _DoText_ triggers the _OnText_ event.
