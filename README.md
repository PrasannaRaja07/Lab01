# Lab01 - QuickSort Profiling and Optimization

## Overview
This repository contains the first lab assignment for the High-Performance Computing (HPC) course. The project demonstrates the implementation of the **QuickSort algorithm** in C to sort an array of 1,000,000 random integers. 

The main objective of this lab is to measure the execution time of the algorithm and perform performance profiling using `gprof` under various GCC compiler optimization levels (`-O2`, `-O3`).

## Repository Contents
- **`mysort.c`**: The C source code implementing the QuickSort algorithm and time measurement logic.
- **`myreport.txt`**: The baseline `gprof` profiling report (compiled without explicit optimization flags).
- **`report_O2.txt`**: Profiling report compiled with the `-O2` optimization flag.
- **`report_O3.txt`**: Profiling report compiled with the `-O3` optimization flag.
- **`report.pdf`**: A detailed document containing the experiment details, analysis of the profiling results, and observations on how compiler optimizations affect performance.
- **`screenshots/`**: A directory containing screenshots of the execution output and profiling steps.

## How to Compile and Run

To compile the code and generate the profiling data yourself, follow these steps:

### 1. Baseline Compilation and Profiling
```bash
# Compile with profiling enabled (-pg)
gcc -pg mysort.c -o mysort

# Run the executable (generates gmon.out)
./mysort

# Generate the profiling report
gprof mysort gmon.out > myreport.txt
```

### 2. Compilation with Optimizations (-O2 / -O3)
To see the effects of optimization, compile with the respective flags:
```bash
# Compile with -O2 optimization
gcc -pg -O2 mysort.c -o mysort_o2
./mysort_o2
gprof mysort_o2 gmon.out > report_O2.txt

# Compile with -O3 optimization
gcc -pg -O3 mysort.c -o mysort_o3
./mysort_o3
gprof mysort_o3 gmon.out > report_O3.txt
```

## Performance Observations
By comparing `myreport.txt`, `report_O2.txt`, and `report_O3.txt`, you can observe how GCC optimizations inline functions (like `swap`), reduce function call overhead, and significantly decrease the overall execution time of the QuickSort algorithm.