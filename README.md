# Indexed File System Simulator

A block-based file system simulator implemented in C++, modeling inode-based storage allocation with direct, single-indirect, and double-indirect block addressing.

This project simulates low-level disk behavior, block allocation, file descriptor management, and multi-level indexed storage — similar to traditional Unix file system designs.

---

## Overview

The system emulates a fixed-size disk and implements:

- File creation, deletion, rename, copy
- File open/close descriptor management
- Read/write operations
- Disk formatting with configurable block size
- Indexed block allocation (direct + single indirect + double indirect)

All disk operations are manually managed at block granularity.

---

## Architecture

### Disk Model
- Fixed-size simulated disk (`DISK_SIM_FILE.txt`)
- Configurable block size
- BitVector for free block tracking

### Inode Structure
Each file is represented by an inode containing:

- 3 direct block pointers
- 1 single-indirect pointer
- 1 double-indirect pointer
- File size metadata
- Block usage tracking

Maximum file size: (3 + block_size + block_size²) × block_size

### Allocation Strategy
- Direct blocks used first
- Then single-indirect indexing
- Then double-indirect indexing
- Manual block zeroing and cleanup
- Full deallocation on file deletion

---

## Implemented Commands

| Command | Operation |
|---------|-----------|
| Format  | Initialize disk with block size |
| Create  | Create new file |
| Open    | Open file (returns FD) |
| Close   | Close file |
| Write   | Write buffer into file |
| Read    | Read file contents |
| Delete  | Remove file and free blocks |
| Copy    | Duplicate file |
| Rename  | Rename file |

---

## Key System Concepts Demonstrated

- Inode-based file system design
- Indexed block allocation
- Free-space management (BitVector)
- Manual disk I/O using `fseek`, `fread`, `fwrite`
- File descriptor lifecycle management
- Resource cleanup and memory handling
- Hierarchical block indexing (direct / single / double)

---

## Build

```bash
g++ main.cpp -o filesystem
```

## Run

```bash
./filesystem
```
