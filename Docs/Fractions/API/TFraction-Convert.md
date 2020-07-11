# Convert method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function Convert(const Multiplier: Int64): TFraction;
```

## Description

This method returns a new fraction whose numerator and denominator are integer multiples of the current fraction. The original and new fractions are equivalent.

The _Multiplier_ parameter specifies the multiplier to be applied. _Multiplier_ must be greater than zero.

### Example

```pascal
var
  F, FConv: TFraction;
begin
  F := TFraction.Create(1, 2);
  FConv := F.Convert(6);         1/2 * 6/6 = 6/12
  Assert((FConv.Numerator = 6) and (FC.Denominator = 12));
  Assert(F = FConv);  // equivalent

  F := TFraction.Create(-5, 13); -5/13 * 3 = -15/39
  FConv := F.Convert(3);
  Assert((FConv.Numerator = -15) and (FC.Denominator = 39));
  Assert(F = FConv);

  F := 0;
  FConv := F.Convert(7);         0/1 * 7/7 = 0/7
  Assert((FConv.Numerator = 0) and (FC.Denominator = 7));
  Assert(F = FConv);

  F := 3;                        3/1 * -3/-3 = -9/-3 = 9/3
  FConv := F.Convert(-3);
  Assert((FConv.Numerator = 9) and (FC.Denominator = 3));
  Assert(F = FConv);
end;
```

## See Also

* [_Simplify_](./TFraction-Simplify.md) method
