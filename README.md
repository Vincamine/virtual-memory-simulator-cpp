# virtual-memory-system-with-simulator-cpp

## Overview
This project is a **Virtual Memory System Simulator** written in C/C++. The simulator models the functionality of a virtual memory system, including address translation, page fault handling, and page replacement. The project completes missing components in the provided simulator, implementing:

1. **Splitting Virtual Addresses** – Extracting VPN (Virtual Page Number) and Offset.
2. **Address Translation** – Mapping virtual addresses to physical addresses using a page table.
3. **Handling Page Faults** – Loading pages into memory and managing page eviction.
4. **Page Replacement Optimization** – Implementing the Clock-Sweep Algorithm for efficient page replacement.

## Project Structure
```
├── src/                    # Source code directory
│   ├── pagetable.c         # Implements address translation
│   ├── pagefault_handler.c # Implements page fault handling
│   ├── process.h           # Defines process structures
│   ├── swapfile.h          # Handles page swapping
│   ├── types.h             # Defines memory-related types
├── workloads/              # Provided memory trace files for testing
├── README.md               # Project documentation
├── Makefile                # Compilation automation
```

## Compilation and Execution
### Compile the Program
To compile the project on a Linux system, use:
```bash
g++ -g -Wall -pedantic -std=c++11 src/*.c -o vm-sim
```
This will generate an executable **vm-sim**.

### Run the Simulator
Execute the simulator with a memory trace file:
```bash
./vm-sim workloads/basic
```
Optional command-line arguments allow configuring memory size and page size:
```bash
./vm-sim -m 32 -p 4 workloads/eviction
```

## Features Implemented
- **Bitwise operations for splitting addresses**
- **Page table lookup for address translation**
- **Page fault handling and swapping**
- **Clock-Sweep Algorithm for page replacement**

## Sample Output
```
Forking new process init. Assigning pid: 0.
Forking new process mozilla. Assigning pid: 1.
...
Virtual Address 00002 (VPN: 00001 OFFSET: 00000)
**** PAGE FAULT at VPN 1. Using free frame PFN 1.
Physical Address 00002 (PFN: 00001 OFFSET: 00000)
STORED 008 as data in virtual address 00002.
...
-----------------------
Statistics:
-----------------------
Reads:                    5
Writes:                   8
Page Faults:              6
Page Fault Rate:   0.461538
```

## Testing
To verify the correctness of the implementation, test with different workloads:
```bash
./vm-sim workloads/everything
./vm-sim workloads/tlb
```

## Notes
- The project follows **x86-style virtual memory principles**.
- The simulator is designed to run on **Linux Khoury machines**.
- All implemented functions are in **pagetable.c** and **pagefault_handler.c**.
- The Clock-Sweep Algorithm efficiently replaces pages with a second-chance mechanism.

## Authors
- Wenxue(Wyllie) Fang

## License
This project is for educational purposes and follows the university's academic integrity policies.