# CompareTo method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
function CompareTo(const F: TFraction): TValueRelationship;
```

## Description

This method compares the current fraction instance with the [_TFraction_](./TFraction.md) given by the _F_. A value is returned that indicates the relationship of the two fractions. The values returned are:

* _EqualsValue_ when the current fraction is equal (equivalent) to _F_.
* _GreaterThanValue_ when the current fraction is greater than _F_.
* _LessThanValue_ when the current fraction is less than _F_.

_EqualsValue_, _GreaterThanValue_ and _LessThanValue_ are defined in the _Types_ unit and have integer values 0, 1 and -1 respectively.

This method can also be used to compare an integer or a floating point to the current fraction simply by passing the integer or floating point value as the _F_ parameter. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point parameter to a [_TFraction_](./TFraction.md) before performing the comparison.

### Note

Fractions are compared by calculating and comparing the 1st and 2nd cross products of the fractions. If the 1st cross product of two fractions,  A and B, is less than the 2nd cross product then fraction A is less than fraction B. If the 1st cross product is greater then the second cross product then fraction A is greater than B. If the two cross products are the same then the fractions are equal.

This means than two fractions that appear to be different may in fact compare equal, for example the 1st and 2nd cross products of `3/4` and `6/8` are both `24`, so `3/4` = `6/8`.

### Example

```pascal
var
  F, F1, F2, F3: TFraction;
begin
  F := TFraction.Create(7, 4);
  F1 := TFraction.Create(1, 2);
  F2 := TFraction.Create(14, 8);
  F3 := TFraction.Create(25, 7);
  Assert(F.CompareTo(F1) = GreaterThanValue);  // 7/4 > 1/2
  Assert(F.CompareTo(F2) = EqualsValue);       // 7/4 = 14/8
  Assert(F.CompareTo(F3) = LessThanValue);     // 7/4 < 25/7
  Assert(F.CompareTo(0.5) = GreaterThanValue); // 7/4 > 0.5
  Assert(F.CompareTo(1.75 = EqualsValue);      // 7/4 = 1.75
  Assert(F.CompareTo(4.76 = LessThanValue);    // 7/4 < 4.76
  Assert(F.CompareTo(1) = GreaterTanValue);    // 7/4 > 1
  Assert(F.CompareTo(2) = LessThanValue);      // 7/4 < 2
end;
```

## See Also

* [_Compare_](./TFraction-Compare.md) class method
* [_Equal_](./TFraction-Equal.md) operator overload
* [_NotEqual_](./TFraction-NotEqual.md) operator overload
* [_LessThan_](./TFraction-LessThan.md) operator overload
* [_LessThanOrEqual_](./TFraction-LessThanOrEqual.md) operator overload
* [_GreaterThan_](./TFraction-GreaterThan.md) operator overload
* [_GreaterThanOrEqual_](./TFraction-GreaterThanOrEqual.md) operator overload
