```
     GGGGGGGGG      GGGG      GGGGGGGGG  GGGGGG   GGGGGG  GGGGGGGGGG
    GGGG            GGGG     GGGG        GGGGGG  GGGGGG  GGGG   GGGG
   GGGG         GGGGGGGGGGGG GGGGGGGGG   G GGGG  G GGGG GGGG    GGGG
   GGGG GGGGGG GGGGGGGGGGGGG GGGGGGGGGG GG GGGG GG GGGG GGGG   GGGGG
  GGGGG  GGGGG GGGGGGGGGGGG  GGGGGGGGG  GG GGGGGG GGGG  GGGG   GGGG
  GGGG   GGGG      GGGG           GGGG  GG  GGGG  GGGG  GGGG   GGGG
   GGGGGGGGGG      GGGG     GGGGGGGGG  GG   GGG   GGGG  GGGGGGGGGG

======================================================================
=====             Geometry plus Simulation modules               =====
=====                     version 20.12 Alpha                    =====
=====                   https://github.com/gismo                 =====
======================================================================
```
## This is an archived version!
This repository includes an archived version of G+Smo (June 3rd, 2021).

# Prerequisites

* Operating systems:
  - MS Windows
  - Linux
  - macOS

* Configuration: [CMake 2.8.12](https://cmake.org) or newer.

* Compilers tested include recent versions of
  - [AMD Optimizing C/C++ Compiler](https://developer.amd.com/amd-aocc/)
  - [AppleClang](https://developer.apple.com/documentation/xcode/) see [here](https://mac.r-project.org/openmp/) for OpenMP support
  - [Clang](https://clang.llvm.org)
  - [GNU GCC](https://gcc.gnu.org)
  - [Intel C++ compiler](https://software.intel.com/content/www/us/en/develop/tools/compilers/c-compilers.html)
  - [Mingw64](http://mingw-w64.org/)
  - [MS Visual Studio C++](https://visualstudio.microsoft.com)
  - [PGI C/C++](https://www.pgroup.com/index.htm) only with `GISMO_WITH_OPENMP=OFF`

* Compilers known to not work
  - [Oracle Developer Studio](https://www.oracle.com/application-development/technologies/developerstudio.html) fails to compile Eigen
  - [IBM XLC C/C++](https://www.ibm.com/products/xl-cpp-linux-compiler-power) fails to compile Eigen

* Recommended:
   - [Doxygen](https://www.doxygen.org) for generating documentation.
   - [Paraview](https://www.paraview.org) for visualization.

# Compilation

The compilation requires configuration using [CMake](https://cmake.org)
at a new, empty folder (in-source builds are disabled).

* On **Linux/macOS**: A Unix makefile exists in the root source
  folder. Running `make` creates a sub folder named `build` and
  executes CMake and compilation inside that folder. Alternatively,
  choose your own build folder and execute CMake pointing to the
  sources.

* On **MS Windows**: MS Visual Studio has [built-in CMake
  support](https://docs.microsoft.com/en-us/cpp/build/cmake-projects-in-visual-studio)
  since version 2015. Alternatively, you can run the `cmake-gui` tool
  (from an environment that is configured with your compiler) to
  generate makefiles (or Visual Studio project files). Then execute
  the make tool to launch compilation. Alternatively, use the
  QtCreator GUI and open the CMakeLists.txt file on the root folder to
  create a QtCreator project.

After successful compilation a dynamic library is created in `./lib` and
executable example programs are output at the `./bin` subdirectory of
the build folder.

Additionally, if [Doxygen](https://www.doxygen.org) is available on
the system one can execute (eg. on Linux):

```make doc```

to obtain the Doxygen documentation in HTML format. The main doxygen
page is at `./doc/html/index.html`.

More information at https://github.com/gismo/gismo/wiki

# Configuration Options

The available options are displayed at CMake configuration.  Short
description and default setting follows:

* CMAKE_BUILD_TYPE        *Release*

  Available values are the standard CMake build configurations: Debug,
Release, RelWithDebInfo, MinSizeRel.

* GISMO_COEFF_TYPE        *double*

  The arithmetic type to be used for all computations. Available options
include double, long double, float.

* GISMO_EXTRA_INSTANCE    *not set*

  If set to one or more of the options available for GISMO_COEFF_TYPE
  the G+Smo library is compiled with extra arithmetic types enabled.

* GISMO_EXTRA_DEBUG       *OFF*

  If set to ON additional debugging tools are enabled during
compilation. These include checked iterators for GCC and MSVC
compilers and call stack back-trace printout when a runtime exception
occurs.

* GISMO_BUILD_LIB         *ON*

  If enabled a dynamic library is created using GISMO_COEFF_TYPE
arithmetic. A target for a static library named gismo_static is also
created but not compiled by default.

* GISMO_BUILD_EXAMPLES    *ON*

  If enabled the programs in the examples folder are compiled, and
executables are created in build-folder/bin.

* GISMO_BUILD_UNITTESTS   *OFF*

  If enabled the tests in the unittests folder are compiled, and an
executable is created in build-folder/bin.

* GISMO_BUILD_AXL         *OFF*

  If enabled the plugin for Axel modeler is compiled (requires Axel).

* GISMO_WITH_PSOLID       *OFF*

  If enabled the extensions using functionalities of Parasolid geometric
kernel are compiled (requires Parasolid).

* GISMO_WITH_ONURBS       *OFF*

  If enabled the extension for reading and writing of Rhinoceros' 3DM is
compiled.

* CMAKE_INSTALL_PREFIX   (system dependent)

  The location for installation of the library, e.g. /usr/local on some
Linux systems.


# Directory structure


The source tree consists of the following sub-folders:

* **src**

Contains all source files. Code is partitioned into modules. Currently
eleven modules are present as sub-folders:

   - **gsCore**
   - **gsMatrix**
   - **gsNurbs**
   - **gsHSplines**
   - **gsModeling**
   - **gsAssembler**
   - **gsSolver**
   - **gsPde**
   - **gsTensor**
   - **gsIO**
   - **gsUtils**

* **examples**

  Examples of usage, small programs and tutorials.

* **unittests**

  Unittests for some parts of the codebase.

* **filedata**

  Data files in the XML format the G+Smo can read and write.

* **extensions**

  Optional additional features that can be compiled along G+Smo.

* **plugins**

   The plugins for:

   - Axel modeler
   - Rhinoceros' 3DM

* **cmake**

  Cmake configuration files.

* **doc**

  Files related to doxygen documentation.

# OS-license

The G+Smo library is distributed under the Mozilla Public License v2.0.  (see [LICENSE.txt](https://github.com/gismo/gismo/blob/stable/LICENSE.txt)).

