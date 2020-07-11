# HasCommonFactor method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function HasCommonFactor(const Factor: Int64): Boolean;
```

## Description

This method checks if a given value is a common factor for the fraction. The value being queried is passed in the _Factor_ parameter.

A common factor is an integer that exactly divides both the numerator and denominator of a fraction.

The method always returns False if _Factor_ is zero.

_HasCommonFactor_ is useful for checking that a value is a valid common factor before passing to _Simplify_ method.

### Example

```pascal
var
  F: TFraction;
  S: string;
  CF: Int64;
begin
  F := TFraction.Create(32, 48);
  // get common factor from user
  S := _;
  if not InputQuery('HasCommonFactor', 'Enter a factor', S) then
    Exit;
  CF := StrToInt64Def(S, 0);
  if F.HasCommonFactor(CF) then
    ShowMessageFmt(
      '%d is a common factor of %d/%d', [CF, F.Numerator, F.Denominator]
    );
end;
```

## See Also

* [_Simplify_](./TFraction-Simplify.md) method
