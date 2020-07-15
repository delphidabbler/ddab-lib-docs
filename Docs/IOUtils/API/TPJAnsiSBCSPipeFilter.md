# TPJAnsiSBCSPipeFilter class

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

## Description

This pipe filter class constructs valid ANSI strings from chunks of data read from a pipe.

An event is triggered for each string read. Strings are also parsed into lines that are divided by a specified end of line marker. Each complete line read is notified to the user via another event.

The class only works for [Single Byte Character Set](http://en.wikipedia.org/wiki/SBCS) (SBCS) strings, i.e. those that take exactly one byte per character. It is the caller's responsibility to interpret the string's code page correctly.

_TPJAnsiSBCSPipeFilter_ descends from [_TPJPipeFilter_](./TPJPipeFilter.md)

### Methods

#### Methods introduced in this class

The only method introduced in this class is an override of _TObject.AfterConstruction_ to set default property values. There is no need to call this method directly.

#### Methods inherited from TPJPipeFilter

| Method | Description |
|--------|-------------|
| [_Create_](./TPJPipeFilter-Create.md) | Object constructor. Sets up object to filter a specified pipe. |
| [_ReadPipe_](./TPJAnsiSBCSPipeFilter-ReadPipe.md) | Reads all available data from the pipe. |
| [_Flush_](./TPJAnsiSBCSPipeFilter-Flush.md) | Flushes any unprocessed buffered data. |
| [_HaveUnprocessedData_](./TPJPipeFilter-HaveUnprocessedData.md) | Checks there is currently any buffered, unprocessed, data. |

### Properties

#### Properties introduced in this class

| Property | Description |
|----------|-------------|
| [_EOLMarker_](./TPJAnsiSBCSPipeFilter-EOLMarker.md) | End of line marker used when parsing text into lines. |

#### Properties inherited from TPJPipeFilter

| Property | Description |
|----------|-------------|
| [_Pipe_](./TPJPipeFilter-Pipe.md) | Read only property providing access to the pipe that is being filtered. |

### Events

| Event | Description |
|-------|-------------|
| [_OnLineEnd_](./TPJAnsiSBCSPipeFilter-OnLineEnd.md) | Event triggered when each end of line is reached. |
| [_OnText_](./TPJAnsiSBCSPipeFilter-OnText.md) | Event triggered whenever valid text is read from pipe. |

No events are inherited.

## Links

* [Classes List](./Classes.md)
