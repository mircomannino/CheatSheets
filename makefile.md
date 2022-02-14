## Makefile cheat sheet

### SHORT DESCRIPTION
Makefile tamplates

### BASIC TEMPLATE
```
CXX = g++
CXXFLAGS = -std=c++11 -c -O3 -I.
SOURCES = main.cpp
OBJECTS = $(SOURCES:.cpp=.o)

all: main

main: $(OBJECTS) assembly.s
    $(CXX) -o $@ $(OBJECTS) assembly.s $(LDFLAGS)

%.o: %.cpp
    $(CXX) $(CXXFLAGS) $< -o $@

.PHONY: clean
clean:
    rm -rf *.o micro_kernel
```                           