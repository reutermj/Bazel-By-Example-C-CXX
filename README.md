# Repository Setup

This stage demonstrates the foundational components of a Bazel repo. While Bazel only requires a `MODULE.bazel` file for a minimal repo setup, this guide follows a more maximalist approach including additional components that follow best practices and improve the developer experience.

## Core Bazel

### MODULE.bazel

The `MODULE.bazel` is the root configuration file for Bazel modules. It is used to declare Bazel module metadata like name, version, and compatibility level and also declare external dependencies and integration.

See more:
* Module documentation: https://bazel.build/external/module
* MODULE.bazel API reference: https://bazel.build/rules/lib/globals/module

### MODULE.bazel.lock

The `MODULE.bazel.lock` is an automatically generated lockfile that records the exact resolved versions of all dependencies determined by Bazel's module resolution process. It contains the complete dependency graph with specific commit hashes, URLs, and integrity checksums for each external dependency used in your project. It ensures reproducible builds by locking dependencies to their exact resolved state, preventing unexpected changes when the same project is built on different machines or at different times. 

See more:
* Lockfile documentation: https://bazel.build/external/lockfile

### .bazelrc

The `.bazelrc` is a configuration file for Bazel command-line flags and options. It is used to declare flags and options that should be consistently applied across the entire project. It enables projects to define specific configurations for different OSes (linux, darwin, windows, etc) and build modes (release, debug, etc).

See more:
* .bazelrc documentation: https://bazel.build/run/bazelrc
* Bazel command line reference: https://bazel.build/reference/command-line-reference

## Bazelisk

Bazelisk is a user-friendly launcher for Bazel. Bazelisk automatically handles the selection, download, and execution of the appropriate Bazel binary.

See more:
* Bazelisk project and documentation: https://github.com/bazelbuild/bazelisk

### Bazelisk wrapper

This guide embeds Bazelisk in the repo (`tools/bazelisk-*`) and provides wrapper scripts (`bazel`, `bazel.bat`) to automatically select the appropriate Bazelisk executable for the host system. This allows users to build a Bazel project without having Bazel installed on their local system.

### .bazelversion

The `.bazelversion` is a configuration file used with Bazelisk. It specifies the exact version of Bazel used to build the project. This helps prevent "works on my machine issues" where the particular version of Bazel on the local system leads to build failures.

See more:
* Bazelisk version algorithm: https://github.com/bazelbuild/bazelisk?tab=readme-ov-file#how-does-bazelisk-know-which-bazel-version-to-run

## Miscellaneous

### .github/renovate.json5

Renovate is a service that automatically creates pull requests to update your project dependencies. This is used to help keep up-to-date your:
* `bazel_dep` dependencies in `MODULE.bazel`
* Bazel version in `.bazelversion`

This helps prevent breaking changes, especially new backwards incompatible flags introduced by Bazel, from piling up and causing a pain when updating.

See more:
* Renovate project: https://docs.renovatebot.com/
* Getting Renovate for your repo: https://docs.renovatebot.com/getting-started/running/
* Renovate's Bazel documentation: https://docs.renovatebot.com/bazel/

## Trying it out

Open this branch in a [Codespace](https://github.com/features/codespaces) by clicking `Code` -> `Codespaces` -> `Create codespace on step1-repo-setup` above, or clone it locally with: `git clone --branch step1-repo-setup https://github.com/reutermj/Bazel-By-Example-C-CXX.git`.

Now lets run our first Bazel command:

```
(Linux/MacOS) ./bazel version
(Windows)     .\bazel.bat version

Bazelisk version: v1.27.0
Bazelisk version: v1.27.0
Build label: 8.3.1
Build target: @@//src/main/java/com/google/devtools/build/lib/bazel:BazelServer
Build time: Mon Jun 30 16:23:40 2025 (1751300620)
Build timestamp: 1751300620
Build timestamp as int: 1751300620
```
