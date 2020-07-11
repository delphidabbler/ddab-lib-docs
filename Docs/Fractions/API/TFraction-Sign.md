# Sign method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function Sign: TValueSign;
```

## Description

This method returns a value representing the sign of the fraction. The return values are:

* _PositiveValue_ - the fraction is positive
* _ZeroValue_ - the fraction is zero
* _NegativeValue_ - the fraction is negative

These values are constants defined in the _Math_ unit as `High(TValueSign)`, `0` and `Low(TValueSign)` respectively. _TValueSign_ is itself defined as `-1..1`.

### Example

```pascal
var
  F: TFraction;
begin
  F := TFraction.Create(2, 3);
  Assert(F.Sign = Math.PositiveValue);
  F := 0;
  Assert(F.Sign = Math.ZeroValue);
  F := TFraction.Create(-2, 3);
  Assert(F.Sign = Math.NegativeValue);
end;
```

### Note

You can also check the sign by using the overloaded `=`, `>` and `<` operators to compare a [_TFraction_](./TFraction.md) to zero, as in:

```pascal
var
  F: TFraction;
begin
  // set up F here
  if F > 0 then
    // positive
  else if F < 0 then
    // negative
  else
  begin
    Assert(F = 0);
    // zero
  end;
```

## See Also

* [_Equal_](./TFraction-Equal.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
