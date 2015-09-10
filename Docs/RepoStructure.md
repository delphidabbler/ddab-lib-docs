# Source Code Repository Structure #

The [Subversion](http://subversion.tigris.org/) repository for the DelphiDabbler Component and Unit Library is structured as follows:

| Directory | Description |
|:----------|:------------|
| <pre style="background-color:transparent;">branches</pre> | Unused at present. |
| <pre style="background-color:transparent;">tags</pre> | Contains copies of all stable releases. |
| <pre style="background-color:transparent;">  lib</pre> | Unused at present. Reserved for any releases of whole library. Each release will have its own sub-directory named `release-x.x.x` where `x.x.x` is the release version number. |
| <pre style="background-color:transparent;">  projects</pre> | Contains stable releases of each sub-project. |
| <pre style="background-color:transparent;">    &lt;project-id&gt;</pre> | Contains stable releases of a sub-project. There is a separate directory for each sub-project whose name is the ID of the sub-project. |
| <pre style="background-color:transparent;">      &lt;release&gt;</pre> | Contains a stable release of the sub-project. There is a separate directory for each release named `release-x.x.x` where `x.x.x` is the release version number. |
| <pre style="background-color:transparent;">      ...</pre> |  |
| <pre style="background-color:transparent;">    ...</pre> |  |
| <pre style="background-color:transparent;">trunk</pre> | Main development tree. Contains the current development code. It is not guaranteed to be stable, but contains the latest updates. |
| <pre style="background-color:transparent;">  common</pre> | Contains files common to more than one project. The directory structure below this level depends on the documents and code files that need to be stored here. |
| <pre style="background-color:transparent;">  lib</pre> | Unused at present. Reserved for any development code and documents relating to the whole library. |
| <pre style="background-color:transparent;">  projects</pre> | Development tree for sub-projects. |
| <pre style="background-color:transparent;">    &lt;project-id&gt;</pre> | Development tree for a sub-project. There is a separate directory for each sub-project whose name is the ID of the sub-project. Any directory structure below this level is project specific. |
| <pre style="background-color:transparent;">    ...</pre> |  |
| <pre style="background-color:transparent;">wiki</pre> | Contains the documents that make up the library's Wiki on Google Code. |

**Links:**

  * Back to [Wiki Home Page](Welcome.md)
