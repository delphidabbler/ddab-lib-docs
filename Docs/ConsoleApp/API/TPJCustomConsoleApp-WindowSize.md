# WindowSize property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property WindowSize: TSize;
```

## Description

This property specifies the size of the window, in pixels, that is used to display a console application. If either dimension is zero or less then the default window size is used.

The property defaults to `(0, 0)`.

## Remarks

If a console application shares a console this property has no effect. See [_UseNewConsole_](./TPJCustomConsoleApp-UseNewConsole.md) for more information about shared consoles.

The individual fields of the property are read-only so the property must be set by first creating a _TSize_ record containing the required window size and then assigning the record to the property. For example:

```pascal
var
  Size: TSize;
  App: TPJConsoleApp;
begin
  // assume App contains a valid TPJConsoleApp instance
  Size.cx := 640;  // 640 pixels wide
  Size.cy := 480;  // 480 pixels high
  App.WindowSize := Size;
end;
```

The [_MakeSize_](./Routines.md#makesize) routine has been provided to make this process easier. The following code has the same effect as the above:

```pascal
var
  App: TPJConsoleApp;
begin
  // assume App contains a valid TPJConsoleApp instance
  App.WindowSize := MakeSize(640, 480);
end;
```

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
