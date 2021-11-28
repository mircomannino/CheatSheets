## CMake cheat sheet

### SHORT DESCRIPTION
CMake is an open-source, cross-platform family of tools designed to build, test and package softwAre.

---

### HOW TO RUN
Your project must contain a ```CMakeList.txt``` file. This file contains all the information to 
create a ```Makefile``` that can be use to compile your source files.
```bash
cmake . 
```
```bash
make
```

---

### BASIC TEMPLATE
Assume to have a basic project-directory, of a project called __HelloCMake__, organized as:
```
HelloCMake
├── bin
├── include
│   ├── header1.hh
│   └── header2.hh
├── src
│   ├── source1.cpp
│   └── source2.cpp
└── test.cpp
```
The simplest way to organize the CMakeList.txt file is the following:
```c++
/* ### File name: test.cpp */
#include "header1.hh"
#include "header2.hh"

int main(int argc, char* argv[]) { /* ...  */ }
```
```cmake
### File name: CMakeList.txt ###

# Project general info
PROJECT( HelloCMake )
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

# Set binary name to compile
SET( test_target test )

# Include directories
include_directories( "./include" )

# Set src files recursively
file( GLOB_RECURSE SRCS "src/*.cpp")

# Set the output directory for binaries
set( EXECUTABLE_OUTPUT_PATH ./bin)

# Add the executable file
add_executable( ${test_target} ${test_target}.cpp ${SRCS})
```
---

### OPENCV TEMPLATE
Assume to have a basic project-directory, of a project called __HelloCMakeOpenCV__, organized as:
```
HelloCMakeOpenCV
├── bin
├── include
│   ├── header1.hh
│   └── header2.hh
├── src
│   ├── source1.cpp
│   └── source2.cpp
└── test.cpp
```
The simplest way to organize the CMakeList.txt file is the following:
```c++
/* ### File name: test_openCV.cpp */
#include "header1.hh"
#include "header2.hh"
#include <opencv2/opencv.hpp>

int main(int argc, char* argv[]) { /* ...  */ }
```
```cmake 
### File name: CMakeList.txt ###

# Project general info
PROJECT( HelloCMakeOpenCV )
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

# Find for required package
find_package( OpenCV REQUIRED )

# Set binary name to compile
SET( test_target test )

# Include directories
include_directories( "./include" )
include_directories( ${OpenCV_INCLUDE_DIRS} )

# Set src files recursively
file( GLOB_RECURSE SRCS "src/*.cpp")

# Set the output directory for binaries
set( EXECUTABLE_OUTPUT_PATH ./bin)

# Add the executable file and linking
add_executable( ${test_target} ${test_target}.cpp ${SRCS})
TARGET_LINK_LIBRARIES( ${test_target} ${OpenCV_LIBS} )
```