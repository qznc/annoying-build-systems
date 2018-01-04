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

### Buck

### Cabal

### CMake

* Custom language

### Gradle

### Grunt

### Jam

### Make

* [Recursive Make Considered Harmful](http://www.lateralt.net/files/auug97.pdf)
* Changes to the Makefile to do not implicitly trigger rebuilds
* Dependencies on directories is not really possible
* Lots of output by default
* Rules with multiple output files are not really possible

### Maven

* Restricting [build lifecycle concept](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)

### Meson

### MS Build

### Ninja

* Very low-level

### NPM

### Python Pip

* The `requirements.txt` can either contain
  the (small) set of direct dependencies
  or the set of all (transitive) requirements for better repeatability.

### Rake

### SBT

* Very slow

### Scons

### Shell Scripts

* Hard to port
* Hard to parallelize (thus slow)
