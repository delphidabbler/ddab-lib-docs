# RoundToMultiple method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function RoundToMultiple(const F: TFraction): TFraction;
```

## Description

This method rounds the fraction to the nearest whole number multiple of the given fraction _F_ and returns the result.

For example, if you round `11/16` to a whole number multiple of `1/8` the result is `6/8`.

_RoundToMultiple_ can be useful if you have performed a calculation using fractions but want the result accurate to a certain degree, for example the nearest eighths or sixteenths. It is also useful for converting floating point numbers to fractions with the required accuracy, for example to express &#960; as a fraction to the nearest seventh.

### Example

Express &#960; in terms of fractions to the nearest 1/N where N = 1 to 10.

```pascal
var
  FPi, FRound: TFraction;
  N: Integer;
begin
  FPi := PI;  // Pi is automatically converted to fraction
  for N := 1 to 10 do
  begin
    FRound := FPi.RoundToMultiple(TFraction.Create(1, N));
    WriteLn(
      Format(
        'Pi in terms of 1/%d = %d/%d',
        [N, FRound.Numerator, FRound.Denominator]
      )
    );
  end;
end;
```

## See Also

* [_TruncateToMultiple_](./TFraction-TruncateToMultiple.md) method
