## Makefile cheat sheet

### SHORT DESCRIPTION
Makefile tamplates

### BASIC TEMPLATE
Assume to have a basic project-directory, organized as:
```
Project
├── main.cpp
├── header.hh
```
Use the following make file to compile:
```
CXX = g++
CXXFLAGS = -std=c++11 -c -O3 -I.
SOURCES = main.cpp
OBJECTS = $(SOURCES:.cpp=.o)

all: main

main: $(OBJECTS)
    $(CXX) -o $@ $(OBJECTS) $(LDFLAGS)

%.o: %.cpp
    $(CXX) $(CXXFLAGS) $< -o $@

.PHONY: clean
clean:
    rm -rf *.o micro_kernel
```                           