# ProcessAttrs property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ProcessAttrs: PSecurityAttributes;
```

## Description

This property specifies the security and inheritance attributes for a console application process. It determines whether the process handle can be inherited by child processes. Setting _ProcessAttrs_ to **nil** means the process handle can't be inherited.

Note that the caller is responsible for setting up the structure correctly. The caller need not maintain a copy of the provided structure once the property is set since an internal copy is made.

The property's default value is **nil**.

## Remarks

To make the process handle inheritable set the _bInheritHandle_ field of the _TSecurityAttributes_ record to _True_. For example:

```pascal
var
  App: TPJConsoleApp;
  Attrs: TSecurityAttributes;
begin
  Attrs.nLength := SizeOf(Security);
  Attrs.lpSecurityDescriptor := nil;
  Attrs.bInheritHandle := True;
  App := TPJConsoleApp.Create;
  try
    App.ProcessAttrs := @Attrs;
    ...
  finally
    App.Free;
  end;
end;
```

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
