# Example 1: Using fixed file information properties

This rather long example shows how to use the Version Information Component's fixed file information properties. It displays descriptions of the properties in a memo. Most of the example is taken up with code that maps fixed file information codes onto descriptive names. The real meat of the example comes in the form creation event handler at the end of the code.

A [similar example](./Example2.md) shows how to achieve the same results using the _[FixedFileInfo](../API/TPJVersionInfo-FixedFileInfo.md)_ property.

Drop a _TMemo_ and a _[TPJVersionInfo](../API/TPJVersionInfo.md)_ component on to a form, create an _OnCreate_ event handler for the form, then enter the following code.

```pascal
type
  TTableEntry = record
    // maps codes to descriptions
    Code: DWORD;
    Desc: string;
  end;

const
  cFileType: array[0..6] of TTableEntry =
  (
    (Code: VFT_APP; Desc: 'Application'),
    (Code: VFT_DLL; Desc: 'DLL'),
    (Code: VFT_DRV; Desc: 'Device driver'),
    (Code: VFT_FONT; Desc: 'Font'),
    (Code: VFT_STATIC_LIB; Desc: 'Static link library'),
    (Code: VFT_VXD; Desc: 'Virtual device driver'),

    (Code: VFT_UNKNOWN; Desc: 'Unknown')
  );

  cFileOSBase: array[0..4] of TTableEntry =
  (
    ( Code: VOS_NT; Desc: 'Windows NT' ),
    ( Code: VOS_DOS; Desc: 'MS-DOS' ),
    ( Code: VOS_OS232; Desc: 'OS2 32 bit' ),
    ( Code: VOS_OS216; Desc: 'OS2 16 bit' ),
    ( Code: VOS_UNKNOWN; Desc: 'Any' )
  );

  cFileOSTarget: array[0..4] of TTableEntry =
  (
    ( Code: VOS__WINDOWS32; Desc: '32 bit Windows' ),
    ( Code: VOS__WINDOWS16; Desc: 'Windows 3.x' ),

    ( Code: VOS__PM32; Desc: 'Presentation Manager 32' ),
    ( Code: VOS__PM16; Desc: 'Presentation Manager 16' ),
    ( Code: VOS__BASE; Desc: 'Unknown' )
  );

function CodeToDesc(Code: DWORD;
  Table: array of TTableEntry): string;
  // return description of code using table
var
  I: Integer;
begin
  Result := '';
  for I := Low(Table) to High(Table) do
    if Table[I].Code = Code then

    begin
      Result := Table[I].Desc;
      Break;
    end;
end;

function FileOSDesc(OS: DWORD): string;
  // describe OS
var
  Target, Base: DWORD;
begin
  // get target and base OS
  Target := OS and $0000FFFF;
  Base := OS and $FFFF0000;
  // build description
  if Base = VOS_UNKNOWN then
    Result := CodeToDesc(Target, cFileOSTarget)
  else if Target = VOS__BASE then

    Result := CodeToDesc(Base, cFileOSBase)
  else
    Result := Format('%s on %s',
      [CodeToDesc(Target, cFileOSTarget),
      CodeToDesc(Base, cFileOSBase)]);
end;

function FileFlagsToStr(Flags: DWORD): string;
  // build string of file flags
const
  cFileFlags: array[0..5] of TTableEntry =
  (
    (Code: VS_FF_DEBUG;        Desc: 'Debug'),
    (Code: VS_FF_PRERELEASE;   Desc: 'Pre-release'),

    (Code: VS_FF_PATCHED;      Desc: 'Patched'),
    (Code: VS_FF_PRIVATEBUILD; Desc: 'Private build'),
    (Code: VS_FF_INFOINFERRED; Desc: 'Inferred'),
    (Code: VS_FF_SPECIALBUILD; Desc: 'Special build')  );
var
  I: Integer;
begin
  Result := '';
  for I := Low(cFileFlags) to High(cFileFlags) do
    if Flags and cFileFlags[I].Code = cFileFlags[I].Code then
      Result := Result + #13#10'   ' + cFileFlags[I].Desc

end;

function VerToStr(Ver: TPJVersionNumber): string;
  // return ver number as string
begin
  Result := Format('%d.%d.%d.%d',
    [Ver.V1, Ver.V2, Ver.V3, Ver.V4]);
end;

procedure TEgForm3.FormCreate(Sender: TObject);
begin
  // clear memo
  Memo1.Lines.Clear;
  // check if we have version info
  if PJVersionInfo1.HaveInfo then
    // we have version info: display fixed file info

    with Memo1.Lines do
    begin
      Add('File Version:'#13#10'   '
        + VerToStr(PJVersionInfo1.FileVersionNumber));
      Add('Product Version:'#13#10'   '
        + VerToStr(PJVersionInfo1.ProductVersionNumber));
      Add('File Flags Mask: '
        + FileFlagsToStr(PJVersionInfo1.FileFlagsMask));
      Add('File Flags: '
        + FileFlagsToStr(PJVersionInfo1.FileFlags));
      Add('File Type:'#13#10'   '

        + CodeToDesc(PJVersionInfo1.FileType, cFileType));
      Add('File sub type:');
      case PJVersionInfo1.FileType of
        VFT_FONT, VFT_DRV, VFT_VXD:
          Add(Format('   %0.8X', [PJVersionInfo1.FileSubType]));
        else Add('   None');
      end;
      Add('File OS:'#13#10'   '
        + FileOSDesc(PJVersionInfo1.FileOS));
    end
  else
    Memo1.Lines.Add('NO VERSION INFO');

end;
```

**Links:**

* Back to the [Examples List](../Examples.md)
* Back to the [Main Component Page](../../VerInfo.md)
