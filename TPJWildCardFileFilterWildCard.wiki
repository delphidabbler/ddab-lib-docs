#summary Description of the TPJWildCardFileFilter.WildCard property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !WildCard property =

*Project:* [DropFilesComponents Drop Files Components].

*Unit:* _PJDropFiles_.

*Class:* _[TPJWildCardFileFilter TPJWildCardFileFilter]_

{{{
property WildCard: string;
}}}

== Description ==

This property filters files based on a wildcard string.

It stores the wildcard that is used by the component to filter files. The wildcard is applied to the base filename or folder name (not the path) and uses the same special characters as DOS and Windows wildcards. The wildcard is applied to both files and folders.

=== Example ===

To filter out all files except those with names beginning with "PJ" and with a `.pas` extension set _!WildCard_ to `'PJ*.pas'`.
