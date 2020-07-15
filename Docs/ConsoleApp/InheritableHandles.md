# [Console Application Runner Classes](../ConsoleApp.md) Inheritable Handles

When we use [_TPJConsoleApp_](./API/TPJConsoleApp.md) to redirect the input and/or output of a child process we create handles to the redirected resources (files or pipes) and pass those handles to the child process. This is done by setting [_TPJConsoleApp_](./API/TPJConsoleApp.md)'s [_StdIn_](./API/TPJCustomConsoleApp-StdIn.md), [_StdOut_](./API/TPJCustomConsoleApp-StdOut.md) and [_StdErr_](./API/TPJCustomConsoleApp-StdErr.md) properties.

The handles are created in the context of the application that is using [_TPJConsoleApp_](./API/TPJConsoleApp.md) and are used in the context of the console application running as a child process. The child process is said to _inherit_ the handles.

A child process can only inherit handles that have been made _inheritable_. This is done by means of the [_TSecurityAttributes_](http://msdn.microsoft.com/en-us/library/aa379560.aspx) structure. This structure is passed to the various Windows API calls used to open files and create pipes and return a handles to them. To ensure that the returned handle is inheritable the _bInheritHandle_ member of the [_TSecurityAttributes_](http://msdn.microsoft.com/en-us/library/aa379560.aspx) record must be set to true.

The following code shows how to do this:


```pascal
var
  Security: TSecurityAttributes;
begin
  Security.nLength := SizeOf(Security);
  Security.lpSecurityDescriptor := nil;
  Security.bInheritHandle := True;
  // ...
  // Pass Security to some API call to create handle
end;
```

You can see concrete examples of using such code in [Appendix 1](./Appendices/Appendix1.md).

File and pipe handles aren't the only ones that can be inherited. There's much more information on [MSDN](http://msdn.microsoft.com/en-us/library/ms683463.aspx).
