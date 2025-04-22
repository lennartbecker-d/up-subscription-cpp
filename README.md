# uProtocol C++  (up-subscription-cpp)

## Welcome!

This library is a uSubscription service written in C++.

*_IMPORTANT NOTE:_ This project is under active development*

## Getting Started

### Requirements:
- Compiler: GCC/G++ 11 or Clang 13
- Conan : 1.59 or latest 2.X

#### Conan packages

Using the recipes found in [up-conan-recipes][conan-recipe-repo], build these
Conan packages:

1. [up-core-api][spec-repo] - `conan create --version 1.6.0-alpha4 --build=missing up-core-api/release`
2. [up-cpp][cpp-api-repo] - `conan create --version 1.0.1-dev --build=missing up-cpp/developer`
3. [zenoh-c][zenoh-repo] - `conan create --version 1.2.1 zenohc-tmp/prebuilt`
4. [zenoh-c][zenoh-repo] - `conan create --version 1.2.1 zenohcpp-tmp/from-source`
5. [up-transport-soecket-cpp][up-transport-socket-cpp-repo] - `conan create --version 1.0.0-dev --build=missing up-transport-socket-cpp/developer`

**NOTE:** all `conan` commands in this document use  Conan 2.x syntax. Please
adjust accordingly when using Conan 1.x.

## How to Use the Library

To add up-subscription-cpp to your conan build dependencies, place following
in your conanfile.txt:

```
[requires]
up-subscription-cpp/[>=1.0.0 <2.0.0]

[generators]
CMakeDeps
CMakeToolchain

[layout]
cmake_layout
```

**NOTE:** If using conan version 1.59 Ensure that the conan profile is
configured to use ABI 11 (libstdc++11: New ABI) standards according to
[the Conan documentation for managing gcc ABIs][conan-abi-docs].

## Building locally

The following steps are only required for developers to locally build and test
up-subscription-cpp, If you are making a project that uses
up-subscription-cpp, follow the steps in the
[How to Use the Library](#how-to-use-the-library) section above.

### With Conan for dependencies

```
cd up-subscription-cpp
conan install . --build=missing
cmake --preset conan-release
cd build/Release
cmake --build . -- -j
```

Once the build completes, tests can be run with `ctest`.

### With dependencies installed as system libraries

**TODO** Verify steps for pure cmake build without Conan.

### Creating the Conan package

See: [up-conan-recipes][conan-recipe-repo]

## Show your support

Give a ⭐️ if this project helped you!

[conan-recipe-repo]: https://github.com/eclipse-uprotocol/up-conan-recipes
[spec-repo]: https://github.com/eclipse-uprotocol/up-spec
[cpp-api-repo]: https://github.com/eclipse-uprotocol/up-cpp
[conan-abi-docs]: https://docs.conan.io/en/1.60/howtos/manage_gcc_abi.html
