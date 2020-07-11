# Compare class method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class function Compare(const A, B: TFraction): TValueRelationship; static;
```

## Description

This class method compares two [_TFraction_](./TFraction.md) instances, _A_ and _B_, and returns a value indicating their relationship. The values returned are:

* _EqualsValue_ when _A_ equals _B_.
* _GreaterThanValue_ when _A_ is greater than _B_.
* _LessThanValue_ when _A_ is less than _B_.

_EqualsValue_, _GreaterThanValue_ and _LessThanValue_ are defined in the _Types_ unit and have integer values 0, 1 and -1 respectively.

This method can also be used to compare an integer or a floating point to a [_TFraction_](./TFraction.md) simply by passing the integer or floating point value as one of the method parameters and a [_TFraction_](./TFraction.md) value as the other parameter. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point parameter to a [_TFraction_](./TFraction.md) before performing the comparison.

### Note

Fractions are compared by calculating and comparing the 1st and 2nd cross products of the fractions. If the 1st cross product of two fractions,  A and B, is less than the 2nd cross product then fraction A is less than fraction B. If the 1st cross product is greater then the second cross product then fraction A is greater than B. If the two cross products are the same then the fractions are equal.

This means than two fractions that appear to be different may in fact compare equal, for example the 1st and 2nd cross products of `3/4` and `6/8` are both `24`, so `3/4` = `6/8`.

### Example

```pascal
var
  F0, F1, F2, F3, F4, F5: TFraction;
  D: Double;
  I: Integer;
begin
  F0 := TFraction.Create(1, 5);
  F1 := TFraction.Create(3, 4);
  F2 := TFraction.Create(6, 8);
  F3 := TFraction.Create(7, 8);
  F4 := TFraction.Create(2, 1);
  F5 := TFraction.Create(25, 7);
  D := 0.75;
  I := 2;
  Assert(TFraction.Compare(F1, F1) = EqualsValue);
  Assert(TFraction.Compare(F1, F2) = EqualsValue);
  Assert(TFraction.Compare(D, F1) = EqualsValue);
  Assert(TFraction.Compare(F4, I) = EqualsValue);
  Assert(TFraction.Compare(F0, F1) = LessThanValue);
  Assert(TFraction.Compare(F3, F5) = LessThanValue);
  Assert(TFraction.Compare(D, F3) = LessThanValue);
  Assert(TFraction.Compare(F2, I) = LessThanValue);
  Assert(TFraction.Compare(F5, F1) = GreaterThanValue);
  Assert(TFraction.Compare(F2, F0) = GreaterThanValue);
  Assert(TFraction.Compare(F3, D) = GreaterThanValue);
  Assert(TFraction.Compare(F5, I) = GreaterThanValue);
end;
```

## See Also

* [_CompareTo_](./TFraction-CompareTo.md) method
* [_Equal_](./TFraction-Equal.md) operator overload
* [_NotEqual_](./TFraction-NotEqual.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
