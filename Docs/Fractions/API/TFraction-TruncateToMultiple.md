# TruncateToMultiple method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function TruncateToMultiple(const F: TFraction): TFraction;
```

## Description

This method truncates the fraction to the nearest whole number multiple of the given fraction _F_ in the direction of zero. It returns the result.

For example, if you truncate `11/16` to a whole number multiple of `1/8` the result is `5/8`.

### Example

This example displays a sequence of ranges of fraction that converge towards &#960;

```pascal
var
  FRangeLo, FRangeHi, FMult, FPi: TFraction;
  N: Integer;
begin
  Memo1.Clear;
  FPi := PI;  // Pi is automatically converted to fraction
  for N := 1 to 20 do
  begin
    FMult := TFraction.Create(1, N);
    FRangeLo := FPi.TruncateToMultiple(FMult);
    FRangeHi := FRangeLo + FMult; // this value will be > Pi
    // Added FMult to FRangeHi simplifies answer, so we un-simplify it
    FRangeHi := FRangeHi.Convert(FRangeLo.Denominator div FRangeHi.Denominator);
    WriteLn(
      Format(
        'Pi in falls in range [%d/%d..%d/%d]',
        [
         FRangeLo.Numerator, FRangeLo.Denominator,
         FRangeHi.Numerator, FRangeHi.Denominator
        ]
      )
    );
  end;
end;
```

## See Also

* [_RoundToMultiple_](./TFraction-RoundToMultiple.md) method
