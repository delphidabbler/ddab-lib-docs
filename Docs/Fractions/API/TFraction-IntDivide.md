# IntDivide operator overload

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class operator IntDivide(const A, B: TFraction): Int64;
```

## Description

This operator overload permits an integer division to be performed on [_TFraction_](./TFraction.md)s using the `div` operator.

The result of the operation is the largest whole number less or equal to the result of dividing _A_ by _B_.

One of the operands may be either an integer or floating point value. The [_Implicit_](./TFraction-Implicit.md) operator takes care of converting the integer and floating point operands to a [_TFraction_](./TFraction.md) before performing the integer division.

The second operand must not be zero. In the case of a [_TFraction_](./TFraction.md) this means the [_Numerator_](./TFraction-Numerator.md) must not be zero.

### Example

```pascal
var
  F1, F2: TFraction;
begin
  // 7/8 div 1/3 = Trunc(7/8 * 3/1) = Trunc(21/8) = 2
  F1 := TFraction.Create(7, 8);
  F2 := TFraction.Create(1, 3);
  Assert(F1 div F2 = 2);

  // 2/3 div 2/3 = Trunc(2/3 * 3/2) = Trunc(6/6) = 1
  F1 := TFraction.Create(2, 3);
  F2 := TFraction.Create(2, 3);
  Assert(F1 div F2 = 1);

  // 5 div 2/3 = Trunc(5/1 * 3/2) = Trunc(15/2) = 7
  F2 := TFraction.Create(2, 3);
  Assert(5 div F2 = 7);

  // 10/3 div 1 = Trunc(10/3 * 1/1) = Trunc(10/3) = 3
  F1 := TFraction.Create(10, 3);
  Assert(F1 div 1 = 3);
end;
```

## See Also

* [_Add_](./TFraction-Add.md) operator overload
* [_Subtract_](./TFraction-Subtract.md) operator overload
* [_Multiply_](./TFraction-Multiply.md) operator overload
* [_Divide_](./TFraction-Divide.md) operator overload
* [_Modulus_](./TFraction-Modulus.md) operator overload
* [_Trunc_](./TFraction-Trunc.md) operator overload
