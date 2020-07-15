# LCD class method

***Project:*** [Fractions](../API.md)

***Unit:*** _DelphiDabbler.Lib.Fractions_

***Record:*** [_TFraction_](./TFraction.md)

***Introduced:*** v0.1

```pascal
class function LCD(const A, B: TFraction): Int64; static;
```

## Description

Returns the least common denominator of the two fraction _A_ and _B_.

### Example

Here's a little procedure that uses _LCD_ and [_Convert_](./TFraction-Convert.md) to convert two fractions to have the same denominator.

```pascal
procedure MakeSameDenominator(var A, B: TFraction);
var
  Common: Int64;
begin
  Common := TFraction.LCD(A, B);
  A := A.Convert(Common div A.Denominator);
  B := B.Convert(Common div B.Denominator);
end;
```

To test this use code such is this:

```pascal
procedure Convert(A, B: TFraction);
begin
  Write(
    Format(
      '%d/%d and %d/%d => ',
      [A.Numerator, A.Denominator, B.Numerator, B.Denominator]
    )
  );
  MakeSameDenominator(A, B);
  WriteLn(
    Format(
      '%d/%d and %d/%d',
      [A.Numerator, A.Denominator, B.Numerator, B.Denominator]
    )
  );
end;

procedure Test;
var
  A, B: TFraction;
begin
  A := TFraction.Create(1, 4);
  B := TFraction.Create(5, 6);
  Convert(A, B);
  A := TFraction.Create(-1, 3);
  B := TFraction.Create(5, 6);
  Convert(A, B);
  A := TFraction.Create(11, 7);
  B := TFraction.Create(3, 5);
  Convert(A, B);
  A := TFraction.Create(3, 8);
  B := TFraction.Create(3, 12);
  Convert(A, B);
end;
```

Running this test program writes the following:

```text
1/4 and 5/6 => 3/12 and 10/12
-1/3 and 5/6 => -2/6 and 5/6
11/7 and 3/5 => 55/35 and 21/35
3/8 and 3/12 => 9/24 and 6/24
```

## See Also

* [_Convert_](./TFraction-Convert.md) method
* [_Simplify_](./TFraction-Simplify.md) methods
