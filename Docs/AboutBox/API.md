# [About Box Component](../AboutBox.md) Programmers' Guide

## Introduction

This section of the _About Box Component_ documentation focusses on describing the usage of components's code.

> **This documentation refers to v3.6 or later of the component only.**
>
> Earlier versions are no longer supported and no documentation is available.

## Contents

There is just one unit in this project, named _PJAbout_, that contains all the code.

_PJAbout_ contains two classes and a few ordinal types, as follows:

| Type | Descriptions |
|------|--------------|
| [_TPJAboutBoxDlg_](./API/TPJAboutBoxDlg.md) | The About Box component itself. |
| _TPJAboutBtnPlacing_ | Determines horizontal placement of OK button in about dialog. This is the type of the [_ButtonPlacing_](./API/TPJAboutBoxDlg-ButtonPlacing.md) property. |
| _TPJAboutBtnKinds_ | Determines caption of about dialog's OK button. This is the type of the [_ButtonKind_](./API/TPJAboutBoxDlg-ButtonKind.md) property. |
| _TPJAboutBtnGlyphs_ | Determines the glyph displayed on about dialog's OK button. This is the type of the [_ButtonGlyph_](./API/TPJAboutBoxDlg-ButtonGlyph.md) property. |
| _TPJAboutPosition_ | Determines whether about dialog's position (centred or offset) is relative to screen, desktop or owning form. This is the type of the [_Position_](./API/TPJAboutBoxDlg-Position.md) property. |
| _TPJAboutBoxForm_ | The form class that implements the actual about box. **Warning:** This class **must not** be accessed directly and is not documented here. The form and it's interface may change without notice and may break any code that relies upon it. |

## Conventions

Identifiers in plain text appear like this: _Identifier_

Identifiers in links appear like this: [_Identifier_](#conventions)

Values and in-line code appear like this:

* `42`
* `'text'`
* `True`
* `X := 42;`

Declarations and source code examples appear syntax highlighted like this:

```pascal
procedure Foo(const Bar: string);
```

## Links

* [Overview](./Overview.md)
