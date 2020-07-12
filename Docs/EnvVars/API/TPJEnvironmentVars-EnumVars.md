# EnumVars class method

***Project:*** [Environment Variables Unit](../API.md)

***Unit:*** _PJEnvVars_

***Class:*** [_TPJEnvironmentVars_](./TPJEnvironmentVars.md)

```pascal
class procedure EnumVars(Callback: TPJEnvVarsEnumEx; Data: Pointer);
```

## Description

Enumerates all the environment variables in the current process.

***Parameters:***

* _Callback_ -- Method or (for Delphi 2009 or later) anonymous procedure of type [_TPJEnvVarsEnumEx_](./TPJEnvVarsEnumEx.md) that is called once for each environment variable and is passed the the environment variable's name and value along with the value of the _Data_ parameter.
* _Data_ -- Pointer passed to _Callback_ each time it is called. The purpose of this value is user-defined and has no meaning to _EnumVars_.

The _Callback_ method or (anonymous procedure) must be implemented by the caller.

> **Important:** Environment variables should not be modified while _EnumVars_ is executing. This is because the method takes a snap-shot of the environment variables before it starts calling _Callback_. Any environment variables added, deleted or modified while _EnumVars_ is running will not be reflected in the enumeration and could cause obscure bugs.

## Examples

Here are two implementation of methods that add the names and values of all environment variables to a user-provided string list.

The first implementation works with all compilers and uses a callback method. The methods we create could be part of any class, but here we assume they are part of a form class named _TForm1_. Implement the following methods:

```pascal
procedure TForm1.EnvVarCallback(const EnvVar: TPJEnvironmentVar; Data: Pointer):
begin
  TStrings(Data).Add(
    Format('Name="%s", Value="%s"', [EnvVar.Name, EnvVar.Value])
  );
end;

procedure TForm1.EnvVarsToStrings(const Strings: TStrings);
begin
  TPJEnvironmentVars.EnumVars(EnvVarCallback, Pointer(Strings));
end;
```

Here our method that adds the environment variables to a given string list is called _EnvVarsToStrings_ and the callback method is _EnvVarCallback_.

In _EnvVarsToStrings_ we call _EnumVars_ and pass a reference to the callback to it. We also pass a pointer to the string list via the _Data_ parameter.

Now _EnumVars_ calls _EnvVarsToStrings_ once for each environment variable, passing the environment variable's details as a [_TPJEnvironmentVar_](./TPJEnvironmentVar.md) value in the _EnvVar_ parameter and the string list pointer in the _Data_ parameter. _EnvVarsToStrings_ casts the _Data_ pointer back to a _TStrings_ object and adds the environment variable's name and value to it.

The second example requires Delphi 2009 or later. We again implement an _EnvVarsToStrings_ method of _TForm1_, but this time we dispense with the callback method and use use an anonymous procedure instead. Here's the method:

```pascal
procedure TForm1.EnvVarsToStrings(const Strings: TStrings);
begin
  TPJEnvironmentVars.EnumVars(
    procedure (const EnvVar: TPJEnvironmentVar; Data: Pointer)
    begin
      SL.Add(
        Format('Name="%s", Value="%s"', [EnvVar.Name, EnvVar.Value])
      );
    end,
    nil
  );
end;
```

Because we are using an anonymous procedure that is in the same scope as _EnvVarsToStrings_'s string list parameter we can access the string list object directly. This means there is no need to pass a reference to the string list to the callback via _EnumVar_'s _Data_ parameter, so we just pass `nil`.
