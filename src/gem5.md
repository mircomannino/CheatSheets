## GEM5 cheat sheet

### m5ops instructions
```m5 ops``` can be used to reset stats and dump stats during simulation. In order to use them, you have to:
1. Build m5 and libm5.a:
    ```bash
    cd gem5/util/m5

    # x86 build
    scons build/x86/out/m5  

    # riscv build
    scons riscv.CROSS_COMPILE=<path/to/riscv64-unknown-linux-gnu-> build/riscv/out/m5 
    ```
2. Include m5ops.h:
    ```c++
    File: test.cpp

    #include <gem5/m5ops.h>
    // Your source code....
    ```
3. Add m5ops instructions in your source code
    ```c++
    File: test.cpp

    // Initialization code...

    m5_reset_stats(0, 0); // Reset stats
    /*
    *   Your region of interest
    */ 
    m5_dump_stats(0, 0); // Dump stats

    // Other code...
    ```
4. Add compiler and linker options to your Makefile
    ```bash
    File: Makefile (riscv)

    CXX = <path/to/riscv-bin-folder>/riscv64-unknown-linux-gnu-g++
    CXXFLAGS = -std=c++17 -c -march=rv64g -mabi=lp64d -O3 -I.
    SOURCES = test.cpp
    OBJECTS = $(SOURCES:.cpp=.o)
    LDFLAGS = -static

    # GEM5 m5ops 
    GEM5_PATH = <path/to/gem5>
    CXXFLAGS += -I$(GEM5_PATH)/include
    LDFLAGS += -L$(GEM5_PATH)/util/m5/build/riscv/out -lm5

    all: test

    test: $(OBJECTS)
        $(CXX) -o $@ $(OBJECTS) $(LDFLAGS)

    %.o: %.cpp
        $(CXX) $(CXXFLAGS) $< -o $@

    .PHONY: clean
    clean:
        rm -rf *.o test
    ```

    ```bash
    File: Makefile (x86)

    CXX = g++
    CXXFLAGS = -std=c++17 -c -O3 -I.
    SOURCES = test.cpp
    OBJECTS = $(SOURCES:.cpp=.o)
    LDFLAGS = -static

    # GEM5 m5ops 
    GEM5_PATH = <path/to/gem5>
    CXXFLAGS += -I$(GEM5_PATH)/include
    LDFLAGS += -L$(GEM5_PATH)/util/m5/build/x86/out -lm5

    all: test

    test: $(OBJECTS)
        $(CXX) -o $@ $(OBJECTS) $(LDFLAGS)

    %.o: %.cpp
        $(CXX) $(CXXFLAGS) $< -o $@

    .PHONY: clean
    clean:
        rm -rf *.o test
    ```

