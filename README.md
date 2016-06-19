# Travis Configs

Travis requires a `.travis.yml` config file in every branch.  The config file
controls how many builds are performed and which configure options each build
should use.

Keeping all these files up-to-date was becoming a problem, so they've been moved
out into a separate repo.

## Build Config Lookup

To build a branch, look for the matching config text file.  If that doesn't
exist, then look for a shorter match.  Finally, if there's no matching config,
use the default.

### Examples

**Branch**: feature/sidebar
- **feature/sidebar.txt** exists

**Branch**: feature5/status-color
- feature5/status-color.txt doesn't exist
- **feature5.txt** exists

**Branch**: coverity
- coverity.txt doesn't exist
- **default.txt** exists

## Building

Travis will perform one build for each line in the config file.  Each line is a
set of options that will be passed to configure.  Any empty line will mean that
**no** options are passed.

## Build Script

The build script makes a few changes to the Makefiles in order to speed things
up.  For example, the docs will not be built.

