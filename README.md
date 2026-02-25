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

Maximum file size:
