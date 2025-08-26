# Hello World

## rules_cc

rules_cc is Bazel's official ruleset providing support for C and C++ programming languages. It provides the rules for building C/C++ executables (`cc_binary`) and libraries (`cc_library`) and running tests (`cc_test`).

## toolchains_cc

toolchains_cc is a Bazel module providing C/C++ toolchain configurations. toolchains_cc simplifies the process of setting up C/C++ toolchains by:

- being easy to configuration with minimal setup required,
- focusing on [hermetic builds](#hermetic-builds) that are reproducible and isolated from the host system, and
- providing cross-platform support for Linux, macOS, and Windows environments.

## BUILD.bazel

BUILD.bazel files are configuration files that mark the root of a [package](https://bazel.build/concepts/build-ref#packages). BUILD.bazel files are used to declare [targets](https://bazel.build/concepts/build-ref#targets) that represent a specific output artifact such as an executable, a library, or a test.

- BUILD file documentation: https://bazel.build/concepts/build-files
- BUILD.bazel API reference: https://bazel.build/rules/lib/globals/build

## Labels

## Trying it out

Open this branch in a [Codespace](https://github.com/features/codespaces) by clicking `Code` -> `Codespaces` -> `Create codespace on step2-hello-world` above, or clone it locally with: `git clone --branch step2-hello-world https://github.com/reutermj/Bazel-By-Example-C-CXX.git`.

Now lets run our first Bazel command:

```
(Linux/MacOS) ./bazel run //packages/hello:hello
(Windows)     .\bazel.bat run //packages/hello:hello
```

```
(Linux/MacOS) ./bazel build //packages/hello:hello
(Windows)     .\bazel.bat build //packages/hello:hello
```

```
(Linux/MacOS) ./bazel run //packages/hello
(Windows)     .\bazel.bat run //packages/hello
```

```
(Linux/MacOS) ./bazel build //...
(Windows)     .\bazel.bat build //...
```

## Hermetic Builds

