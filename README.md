# Assembly Symbol Dumper
[![Build Status](https://github.com/devon-artmeier/dumpasmsym/actions/workflows/cmake-multi-platform.yml/badge.svg)](https://github.com/devon-artmeier/dumpasmsym/actions/workflows/cmake-multi-platform.yml)

This is a tool to extract symbols from Assembly output files.

## Supports

* Binary files generated from this tool
* Psy-Q symbol files
* vasm vobj files
* vasm vlink symbol files (default format only)

## Usage

    dumpasmsym -o [output] <-m [mode]> <-v [type]> <-b [base]> <-iy [symbol]> <-xy [symbol]>
               <-ip [prefix]> <-xp [prefix]> <-is [suffix]> <-xs [suffix]> [input files]
    
        -o [output]     - Output file
        <-m [mode]>     - Output mode
                          bin - Binary (default)
                          asm - Assembly
                          c   - C
        <-v [type]>     - Value type (TEXT OUTPUT MODE ONLY)
                          u32 - Unsigned 32-bit (default)
                          u64 - Unsigned 64-bit
                          s32 - Signed 32-bit
                          s64 - Signed 64-bit
        <-b [base]>     - Numerical system (TEXT OUTPUT MODE ONLY)
                          hex - Hexadecimal (default)
                          dec - Decimal
                          bin - Binary
        <-iy [symbol]>  - Only include symbol
        <-xy [symbol]>  - Exclude symbol
        <-ip [prefix]>  - Only include symbols with prefix
        <-xp [prefix]>  - Exclude symbols with prefix
        <-is [suffix]>  - Only include symbols with suffix
        <-xs [suffix]>  - Exclude symbols with suffix
        [input files]   - List of input files

## Build Instructions

CMake is required to build this.

* On Windows, you can run "make.bat" and the built executable will be put in the "out/bin" folder.
* On other systems, you can call "make" and then "make install".

## Binary Output Format

    Little endian
    
    Signature ("BSYM", 4 bytes)
    Number of symbols (4 bytes)
    For each symbol:
        Name character count (1 byte)
        Name string data
        Value (8 bytes)
    Number of input file names (4 bytes)
    For each input file name:
        File name character count (1 byte)
        File name string data
