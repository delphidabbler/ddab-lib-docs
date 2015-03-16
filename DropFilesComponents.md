<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Drop Files Components #

The drop files components comprise two units: _PJDropFiles_ and _PJDropFilesDsgn_.

## PJDropFiles ##

This unit provides three components that support drag and drop from Windows Explorer along with subsidiary components that can filter dropped files. The components are:

| **Class** | **Description** |
|:----------|:----------------|
| _[TPJDropFiles](TPJDropFiles.md)_ | Container control that catches files dragged and dropped onto its client area or the client area of child controls. |
| _[TPJFormDropFiles](TPJFormDropFiles.md)_ | Non-visual component that catches files dragged and dropped from Explorer onto the form that contains the component. |
| _[TPJCtrlDropFiles](TPJCtrlDropFiles.md)_ | Non-visual component that catches files dragged and dropped from Explorer onto an associated control. |
| _[TPJExtFileFilter](TPJExtFileFilter.md)_ | File filter component that filters files according to their extension. |
| _[TPJWildCardFileFilter](TPJWildCardFileFilter.md)_ | File filter component that filters files according to a DOS-style wild card. |
| _[TPJFileFilter](TPJFileFilter.md)_ | An abstract base class for file filter components. |

Other documented types are:
| **Type** | **Description** |
|:---------|:----------------|
| _[TPJDropFilesOption and TPJDropFilesOptions](TPJDropFilesOptionsSet.md)_ | Enumerated type and set that define the possible values of the _Options_ property of the drop files components. |
| _[TPJDroppedFileFilter](TPJDroppedFileFilter.md)_ | Type of _OnFileFilter_ events of drop files components. |
| _[TPJExtFileFilterStyle](TPJExtFileFilterStyleEnum.md)_ | Enumeration representing the kind of filtering performed by the _[TPJExtFileFilter.Style](TPJExtFileFilterStyle.md)_ property. |

The unit also contains undocumented support code and helper classes that are not designed for public use.

## PJDropFilesDsgn ##

This unit contains the design time elements of the drop files components: a component editor, a property editor and the component and editor registration code.

The editors are:

| **Editor class** | **Description** |
|:-----------------|:----------------|
| _TPJExtFileFilterExtPE_ | Property editor for the _[Extensions](TPJExtFileFilterExtensions.md)_ property of the _[TPJExtFileFilter](TPJExtFileFilter.md)_ component. This editor displays a dialog box where extensions can be added, removed and saved in the correct format. |
| _TPJDropFilesCE_ | Component editor that causes an event handler for the _OnDropFiles_ events of the drop file components to be opened in the designer when the components are double-clicked. The default action without this component editor is to open the rarely used _OnBeforeDrop_ event handler, which is not very useful. |

**Links:**

  * Back to [Wiki Home Page](Welcome.md)
  * [Drop Files Components Web Page](http://www.delphidabbler.com/software/dropfiles).