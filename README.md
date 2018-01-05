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

### Shake

* Requires Haskell (GHC)

### Shell Scripts

* Hard to port
* Hard to parallelize (thus slow)

### Tup

### Xmake
