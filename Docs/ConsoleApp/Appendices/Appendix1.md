# [Console Application Runner Classes](../../ConsoleApp.md)  Appendix 1: Creating inheritable handles

This appendix contains some example code that can be used to create [inheritable handles] to files and pipes.

> If you don't want to get involved with all this low level stuff you can just use _TPJPipe_ and _TPJFileHandle_ from the [I/O Utility Classes](../../IOUtils.md) to open pipes and files respectively with inheritable handles.

## Pipes

Pipes have two handles: a write handle used to write data into the pipe and a read handle to read data out of the other end. Here's a little routine to open an un-named pipe of a given size with inheritable handles. If the size is given as `0` then a pipe with default size is created.

```pascal
procedure CreatePipe(out ReadHandle, WriteHandle: THandle; const Size: LongWord = 0);
var
  Security: TSecurityAttributes;  // file's security attributes
begin
  // Set up security structure so file handle is inheritable
  Security.nLength := SizeOf(Security);
  Security.lpSecurityDescriptor := nil;
  Security.bInheritHandle := True;
  if not Windows.CreatePipe(ReadHandle, WriteHandle, @Security, Size) then
    raise Exception.CreateFmt(
      'Can_t create pipe: "%s"', [SysErrorMessage(GetLastError)]
    );
end;
```

## Files

Files have a single handle. Whether the handle is used for reading or writing the file (or both) depends on how it was opened.

Two routines are presented. The first opens an existing file for reading while the second creates a new empty file for writing. There are other possibilities of course, such as opening an existing file for appending, which are not covered here. However the implementations are very similar.

### Open file for reading

This example could be used to get a handle suitable for use in redirecting a console application's standard input to a file. You would assign the handle to [_TPJConsoleApp_](../API/TPJConsoleApp.md)'s [_StdIn_](../API/TPJCustomConsoleApp-StdIn.md) property.

```pascal
function OpenInputFile(const FileName: string): THandle;
var
  Security: TSecurityAttributes;  // file's security attributes
begin
  // Set up security structure so file handle is inheritable (NT)
  Security.nLength := SizeOf(Security);
  Security.lpSecurityDescriptor := nil;
  Security.bInheritHandle := True;
  // Open the file for reading
  Result := CreateFile(
    PChar(FileName),        // file name
    GENERIC_READ,           // readable file
    FILE_SHARE_READ,        // share read access
    @Security,              // security attributes (NT only)
    OPEN_EXISTING,          // file must exist
    FILE_ATTRIBUTE_NORMAL,  // just the normal attributes
    0                       // no template file (NT only)
  );
  if Result = INVALID_HANDLE_VALUE then
    raise Exception.CreateFmt('Can_t open file "%s"', [FileName]);
end;
```

### Create new file for writing

If you want to redirect a console application standard output or standard error to a file, this routine provides a suitable handle for assignment to [_TPJConsoleApp_](../API/TPJConsoleApp.md)'s [_StdOut_](../API/TPJCustomConsoleApp-StdOut.md) or [_StdErr_](../API/TPJCustomConsoleApp-StdErr.md) properties.

```pascal
function CreateOutputFile(const FileName: string): THandle;
var
  Security: TSecurityAttributes;  // file's security attributes
begin
  // Set up security structure so file handle is inheritable (NT)
  Security.nLength := SizeOf(Security);
  Security.lpSecurityDescriptor := nil;
  Security.bInheritHandle := True;
  // Create new empty file
  Result := CreateFile(
    PChar(FileName),        // file name
    GENERIC_WRITE,          // writeable file
    0,                      // no sharing
    @Security,              // security attributes (NT only)
    CREATE_ALWAYS,          // always create the file, even if exists
    FILE_ATTRIBUTE_NORMAL,  // just the normal attributes
    0                       // no template file (NT only)
  );
  if Result = INVALID_HANDLE_VALUE then
    raise Exception.CreateFmt('Can_t create file "%s"', [FileName]);
end;
```

To open a file for appending, or to create it if it doesn't exist, replace `CREATE_ALWAYS` above with `OPEN_ALWAYS`.

## Links

* [Appendix 2](./Appendix2.md)
* [Appendicies](../Appendices.md)
