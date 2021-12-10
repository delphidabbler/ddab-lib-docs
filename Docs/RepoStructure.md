# Source Code Repository Structure 

The [Subversion repository](https://sourceforge.net/p/ddablib/code/HEAD/tree/)
for the DelphiDabbler Component and Unit Library is structured as follows:

| Directory | Description |
|:----------|:------------|
| `branches` | Unused at present. |
| `tags` | Contains copies of all stable releases. |
| `tags/lib` | Unused at present. Reserved for any releases of whole library. Each release will have its own sub-directory named `release-x.x.x` where `x.x.x` is the release version number. |
| `tags/projects` | Contains stable releases of each sub-project. |
| `tags/projects/<id>` | Contains stable releases of a sub-project. There is a separate directory for each sub-project whose name is the ID of the sub-project. |
| `tags/projects/<id>/<release>` | Contains a stable release of the sub-project. There is a separate directory for each release named `release-x.x.x` where `x.x.x` is the release version number. |
| `trunk` | Main development tree. Contains the current development code. It is not guaranteed to be stable, but contains the latest updates. |
| `trunk/common` | Contains files common to more than one project. The directory structure below this level depends on the documents and code files that need to be stored here. |
| `trunk/lib` | Unused at present. Reserved for any development code and documents relating to the whole library. |
| `trunk/projects` | Development tree for sub-projects. |
| `trunk/projects/<id>` | Development tree for a sub-project. There is a separate directory for each sub-project whose name is the ID of the sub-project. Any directory structure below this level is project specific. |

**Links:**

  * Back to [Wiki Home Page](Welcome.md)
