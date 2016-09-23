# Resource File Unit Constants #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

Some constants are defined to assist in setting some of the class properties.

## Memory Flags Constants ##

The following flags are used to form the bitmask in a resource entry's _MemoryFlags_ property. The first four constants in the table can or ORd together to form the bitmask. The final three constants are complements of the first three and are ANDed against the bitmask to remove their complement from it.

| **Constant** | **Value** | **Description** |
|:-------------|:----------|:----------------|
| `RES_MF_MOVEABLE` | `$0010` | The system can move the resource in memory. If this flag is not present the resource is fixed in memory. |
| `RES_MF_PURE` | `$0020` | The resource contains DWORD aligned data so that padding is not required. If this flag is not present the resource is not DWORD aligned and must be padded. |
| `RES_MF_PRELOAD` | `$0040` | The resource is to be loaded in memory just after the application itself has been loaded. If not present then loading of the resource may be deferred until required by the application. |
| `RES_MF_DISCARDABLE` | `$1000` | If set then on low memory conditions, the resource can be removed from memory and then reloaded when the application needs it, otherwise the resource must remain in memory. |
| `RES_MF_FIXED` | `$FFEF` | Complement of RES\_MF\_MOVEABLE: used to remove this flag from the bitmask. |
| `RES_MF_IMPURE` | `$FFDF` | Complement of RES\_MF\_IMPURE: used to remove this flag from the bitmask. |
| `RES_MF_LOADONCALL` | `$FFBF` | Complement of RES\_MF\_LOADONCALL: used to remove this flag from the bitmask. |

Note that Windows NT ignores `RES_MF_MOVEABLE`, `RES_MF_IMPURE` and `RES_MF_PRELOAD`.

## Predefined Resource Types ##

Delphi's _Windows_ unit defines all the predefined resources types known at the time of writing except `RT_HTML` and `RT_MANIFEST`. Therefore these two type identifiers are defined in this unit for convenience:

* `RT_HTML = MakeIntResource(23);`
* `RT_MANIFEST = MakeIntResource(24);`

See Windows documentation for a description of all the predefined resource types.
