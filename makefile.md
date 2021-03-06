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
TARGET = main
LIBS = -lm
CC = g++
CFLAGS = -g -Wall

.PHONY: default all clean

default: $(TARGET)
all: default

OBJECTS = $(patsubst %.cpp, %.o, $(wildcard *.cpp))
HEADERS = $(wildcard *.h)

%.o: %.c $(HEADERS)
    $(CC) $(CFLAGS) -c $< -o $@

$(TARGET): $(OBJECTS)
    $(CC) $(OBJECTS) -Wall $(LIBS) -o $@

clean:
    -rm -f *.o
    -rm -f $(TARGET)
```                           