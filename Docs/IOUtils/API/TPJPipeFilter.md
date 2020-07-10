# TPJPipeFilter class

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

## Description

This is an abstract base class for all classes that filter data read from pipes. It defines common methods and properties along with some abstract methods to be overridden in sub classes.

### Methods

#### Protected

| Method | Description |
|--------|-------------|
| [_LeftOverByteCount_](./TPJPipeFilter-LeftOverByteCount.md) | _Abstract_. Must return number of bytes of data that cannot be processed yet. |
| [_DoFilter_](./TPJPipeFilter-DoFilter.md) | _Abstract_. Performs filtering operation on data. |
| [_DoFlush_](./TPJPipeFilter-DoFlush.md) | _Abstract_. Flushes any buffered data. |

#### Public

| Method | Description |
|--------|-------------|
| [_Create_](./TPJPipeFilter-Create.md) | Object constructor. Sets up object to filter a specified pipe. |
| [_ReadPipe_](./TPJPipeFilter-ReadPipe.md) | Reads all available data from the pipe. |
| [_Flush_](./TPJPipeFilter-Flush.md) | Flushes any unprocessed buffered data. |
| [_HaveUnprocessedData_](./TPJPipeFilter-HaveUnprocessedData.md) | Checks there is currently any buffered, unprocessed, data. |

### Properties

| Property | Description |
|----------|-------------|
| [_Pipe_](./TPJPipeFilter-Pipe.md) | Read only property providing access to the pipe that is being filtered. |

### Events

_TPJPipeFilter_ exposes no events.

## Links

* [Classes List](./Classes.md)
