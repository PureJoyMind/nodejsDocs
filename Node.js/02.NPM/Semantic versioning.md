# What Is Semantic Versioning

***For more details on what semantic versioning is, refer to [the official website](https://semver.org/).***

Also called "SemVer". A version of a node package has 3 numbers:

1.  Major version
2.  Minor version
3.  Patch version/release

***`<package> Major.Minor.Patch`***
1. Patch Version: Is the bug fixed versions
2. Minor Version: Used for adding new features that don't break the existing api
3. Major Version: if we add a new feature that could potentially break the existing applications that depend apon the current package then we'll increase the major version.

### Caret Character "^"
`^M.m.p`
Tells npm that we are intrested in any version of the package as long as the major version is still M, not any newer or older major version.
**The alternative syntax to this is:**
`M.x` or if we want a little more specific version with the minor version too, `M.m.x` or `~M.m.p`

***We can also only use an exact version of a package by not using "~ or ^" at all.***
