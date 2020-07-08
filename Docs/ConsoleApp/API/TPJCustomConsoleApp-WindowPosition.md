# WindowPosition property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property WindowPosition: TPoint;
```

## Description

This property specifies the co-ordinates of the top left corner of a console application's window, in pixels. If either co-ordinate is negative then the default window position is used.

The property defaults to `(-1, -1)`.

## Remarks

If a console application shares a console this property has no effect. See [_UseNewConsole_](./TPJCustomConsoleApp-UseNewConsole.md) for more information about shared consoles.

The individual fields of the property are read-only so the property must be set by first creating a _TPoint_ record containing the required position information and then assigning the record to the property. For example:

```pascal
var
  Pt: TPoint;
  App: TPJConsoleApp;
begin
  // assume App contains a valid TPJConsoleApp instance
  Pt.X := 200;
  Pt.Y := 400;
  App.WindowPosition := Pt;
end;
```

Use of the VCL's _Point_ routine makes this process easier. The following code has the same effect as the above:

```pascal
var
  App: TPJConsoleApp;
begin
  // assume App contains a valid TPJConsoleApp instance
  App.WindowPosition := Point(200, 400);
end;
```

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
