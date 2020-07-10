# Classes

***Project:*** [I/O Utility Classes](../API.md)

The following classes are included in the project:

| Class | Unit | Description |
|-------|------|-------------|
| [_TPJPipe_](./TPJPipe.md) | [_PJPipe_](./PJPipe.md) | This class encapsulates an un-named pipe. It simplifies read and writing such pipes and creating pipes with inheritable handles. |
| [_TPJFileHandle_](./TPJFileHandle.md) | [_PJFileHandle_](./PJFileHandle.md) | This class can create or open files in various access and sharing modes with specified security and provide access to the file handle. It makes it easy to create or open files with inheritable handles. |
| [_TPJPipeFilter_](./TPJPipeFilter.md) | [_PJPipeFilters_](./PJPipeFilters.md) | Abstract base class for all classes that filter data read from pipes. |
| [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md) | [_PJPipeFilters_](./PJPipeFilters.md) | Pipe filter that constructs valid ANSI strings from data read from pipe. Strings are also parsed into lines. Only single byte character sets are supported. |
| [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md) | [_PJPipeFilters_](./PJPipeFilters.md) | Pipe filter that constructs valid Unicode strings from data read from pipe. Strings are also parsed into lines. Only characters from Unicode's basic multilingual plane are supported. |
