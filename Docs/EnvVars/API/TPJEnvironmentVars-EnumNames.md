# EnumNames class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class procedure EnumNames(Callback: TPJEnvVarsEnum; Data: Pointer);
```

## Description

Enumerates the names of all the environment variables in the current process.

***Parameters:***

* _Callback_ -- Method or (for Delphi 2009 or later) anonymous procedure of type [_TPJEnvVarsEnum_](./TPJEnvVarsEnum.md) that is called once for each environment variable and is passed the the environment variable's name and the value of the _Data_ parameter.
* _Data_ -- Pointer passed to _Callback_ each time it is called. The purpose of this value is user-defined and has no meaning to _EnumNames_.

The _Callback_ method or (anonymous procedure) must be implemented by the caller.

> **Important:** Environment variables should not be modified while _EnumNames_ is executing. This is because the method takes a snap-shot of the environment variable names before it starts calling _Callback_. Any environment variables added or deleted while _EnumNames_ is running will not be reflected in the enumeration and could cause obscure bugs.

## Examples

Here are two implementation of methods that add the names of all environment variables to a user-provided string list.

The first implementation works with all compilers and uses a callback method. The methods we create could be part of any class, but here we assume they are part of a form class named _TForm1_. Implement the following methods:

```pascal
procedure TForm1.EnvNameCallback(const VarName: string; Data: Pointer):
begin
  TStrings(Data).Add(VarName);
end;

procedure TForm1.EnvNamesToStrings(const Strings: TStrings);
begin
  TPJEnvironmentVars.EnumNames(EnvNameCallback, Pointer(Strings));
end;
```

Here our method that adds the environment variable names to a given string list is called _EnvNamesToStrings_ and the callback method is _EnvNameCallback_.

In _EnvNamesToStrings_ we call _EnumNames_ and pass a reference to the callback to it. The interesting bit is that we pass a pointer to the string list via the _Data_ parameter.

Now _EnumNames_ calls _EnvNamesToStrings_ once for each environment variable, passing the environment variable's name in the _VarName_ parameter and the string list pointer in the _Data_ parameter. _EnvNamesToStrings_ casts the _Data_ pointer back to a _TStrings_ object and adds the environment variable name to it.

The second example requires Delphi 2009 or later. We again implement an _EnvNamesToStrings_ method of _TForm1_, but this time we dispense with the callback method and use use an anonymous procedure instead. Here's the method:

```pascal
procedure TForm1.EnvNamesToStrings(const Strings: TStrings);
begin
  TPJEnvironmentVars.EnumNames(
    procedure (const AName: string; Data: Pointer)
    begin
      SL.Add(AName);
    end,
    nil
  );
end;
```

Because we are using an anonymous procedure that is in the same scope as _EnvNamesToStrings_'s string list parameter we can access the string list object directly. This means there is no need to pass a reference to the string list to the callback via _EnumName_'s _Data_ parameter, so we just pass `nil`.
