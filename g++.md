## g++ cheat sheet
Cheat sheet of g++ compilation flags.

#### MOST COMMON
* ```-version``` Shows the version of g++
* ```-Wall``` Shows all the warnings during compilation
* ```-g``` Produces debug information for your code. It can be used with [gdb](https://github.com/mircomannino/CheatSheets)
* ```--std=c++<N>``` Uses the version \<N\> of C++ during compilation.
* ```-o <filename>``` Compiles and links file into an executable named \<filename\>
* ```-c``` Compiles and assembles files without linking them. 

#### OPTIMIZATION FLAGS
Each of the following flags enable/disable a set of other flags. Please look at the [official page](https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html) for details.
* ```-O0``` Reduces compilation time and make debugging produce the expected results. It is the default optimization flag.
* ```-O1```
* ```-O2``` GCC performs nearly all supported optimizations that do not involve a space-speed tradeoff.
* ```-O3``` Optimize yet more.
* ```-Os``` Optimize for size. It enables all the ```-O2``` flags except those that often increase code size.
* ```-Ofast``` Disregard strict standards compliance.
* ```-Og``` Optimize debugging experience.