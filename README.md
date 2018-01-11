# Annoying Build Systems

Many people complain about many build (and packaging) systems.
This repo tries to collect the annoyances
in a similar fashion to
[awesome lists](https://github.com/sindresorhus/awesome).

To contribute, send pull requests.
The Licence for this repo is [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

## Builds Systems and their Annoyances

### Ant

* Looks like Make with XML syntax

### Bazel

* Can not have external dependencies

### Buck

* Can not have external dependencies

### Cabal

### Cargo

* Assumes build machine is networked; no obvious way to pre-download dependencies and have them be used

### CMake

* Custom language
* Lacking documentation
* "so huge and bloated, compilation takes longer than compiling GCC (!). It’s not even possible to create freestanding Makefiles, since the generated Makefiles call back into the cmake binary itself." [source](https://suckless.org/sucks/)

### Fabricate

### Gradle

* Changes to `build.gradle` do not implicitly trigger rebuilds
* If you do not know Groovy the syntax can be confusing

### Gyp

* JSON syntax with condition code as strings

### Grunt

### Jam

### Make alone

* [Recursive Make Considered Harmful](http://www.lateralt.net/files/auug97.pdf)
* Changes to the Makefile do not implicitly trigger rebuilds
* Dependencies on directories is not really possible
* Lots of output by default
* Rules with multiple output files are not really possible
* [can't handle spaces in pathnames](https://savannah.gnu.org/bugs/?712)
* Uses a POSIX/bash shell, which hurts portability

### Make with Autotools

* Obscure m4 macro language
* Posix-only
* Hard to debug because of generated code
* [Configure does many unnecessary checks](https://varnish-cache.org/docs/2.1/phk/autocrap.html)

### Maven

* Restricting [build lifecycle concept](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
* Throws Null Pointer Exceptions and gives a stack trace for simple errors such as missing parameters
* Verbose logs
* Uses XML (possibly annoying), does not support XML attributes (annoying)

### Meson

### MS Build

### Ninja

* Very low-level
* All goals are treated as files (no equivalent to Make's PHONY)

### NPM

* `npm install` [can be dangerous](https://github.com/joaojeronimo/rimrafall)
* [Replicates transitive dependencies](https://lexi-lambda.github.io/blog/2016/08/24/understanding-the-npm-dependency-model/)
* No way to specify test-only, build-only, debug-only, or CI-only dependencies ([source](https://lobste.rs/s/5ms7mb/what_is_annoying_about_certain_build#c_rl6qct))
* Native add-ons make artifacts non-portable

### Pants

* Can not have external dependencies

### Python Pip

* The `requirements.txt` can either contain
  the (small) set of direct dependencies
  or the set of all (transitive) requirements for better repeatability.

### Rake

### SBT

* Very slow
* Builds a directory tree on startup. If SBT is started in the `/` directory it [runs out of memory](https://github.com/sbt/sbt/issues/1458)
* Uses a hard to understand [multilayered mutable execution model](http://www.lihaoyi.com/post/SowhatswrongwithSBT.html)
  "The problems I discussed in this post are deep.
  These aren't things you can 'just send a PR' or 'just help them fix it'.
  They are fundamental to what SBT is."

### Scons

* Too slow for larger projects ([source](https://www.reddit.com/r/programming/comments/gm1dy/stop_inventing_motherfucking_build_systems/c1okqt7/))
* [VariantDir is confusing](https://stackoverflow.com/a/1074587)

### Shake

* Requires Haskell (GHC)

### Shell Scripts

* Hard to port
* Hard to parallelize (thus slow)

### Tup

### Xmake

### Yocto

Yocto builds Linux distributions by invoking other build systems. It has many unique features:

* To use it, you [must](http://www.yoctoproject.org/docs/current/ref-manual/ref-manual.html#structure-core-script) source a shellscript, breaking Fish compatibility.
* Officially supported distros are [whitelisted](http://www.yoctoproject.org/docs/current/ref-manual/ref-manual.html#detailed-supported-distros): Its fakeroot implementation routinely breaks because Glibc is too new. Therefore, it must often be used in Docker or other containerization on unsupported distributions.
* Compiling the wrong code: There is a setting of whether to compile the local or remote copy of each repository, but changing the setting is not in all cases respected before a clean build is made.
* Flimsy developer essentials that regularly stop working: Yocto has a concept of a [devshell](http://www.openembedded.org/wiki/Devshell): This opens a *terminal* (of all things) with the build environment set up in the build directory of a particular repository (for building only that one). Getting this working through Docker or other containerization really *depends* (if you're not careful, it may attempt to start X in your container, which will hang your existing X). As if its interactions with your Linux desktop isn't surprising enough as it is: You may be working in Konsole in an X session … but the devshell window that pops up is a Gnome-terminal in Weston in a different VT.
* If you try to work outside devshell: Pulling dependencies while building is a sure way to distract your edit-compile-debug cycle with unrelated breakages from elsewhere, as well as the occasional big change that takes ages to rebuild.
* Bitbake recipes:
  - Look like shellscripts with improper quoting. Disgust.
  - Have their own variables that look like shell variables. Confusing & error prone.
  - Use magically named flat variables instead of structured data. Requires disciplined adherence to documented best practices.
