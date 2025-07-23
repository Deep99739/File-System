```
SimpleFS — A Minimal Unix-Style File System
==========================================

Overview
--------
SimpleFS is an educational, user–space re-implementation of core Unix File
System ideas.  It is organised into three layers:

1. **Shell (src/shell/sfssh.cpp)** – A small interactive program that converts
   user commands into file-system calls (`debug`, `format`, `mount`, `create`,
   `read`, `write`, `stat`, `remove`, `copyin`, `copyout`).

2. **File System (src/library/fs.cpp)** – Your implementation.  It manages
   on-disk data structures (superblock, inode table, free-block bitmap, data
   blocks) and performs all bookkeeping required for persistence.

3. **Disk Emulator (src/library/disk.cpp)** – Wraps a normal file (the *disk
   image*) and exposes 4096-byte block reads/writes so that the file system
   behaves as if it were talking to real hardware.

Key Features Implemented
------------------------
* Superblock creation, verification, and pretty-printing (`debug`, `format`,
  `mount`).
* Inode allocation, de-allocation, and metadata updates (`create`, `remove`,
  `stat`).
* Block allocation via a free-block bitmap; supports direct and single-indirect
  data blocks.
* Buffered, offset-aware file I/O with automatic block growth (`read`, `write`).


File-System Commands
--------------------
* **format**   Initialise a brand-new disk image (wipes existing data).
* **mount**    Load superblock, verify parameters, build free-block bitmap.
* **debug**    Print human-readable superblock and inode table information.
* **create**   Allocate a fresh inode and make it available for use.
* **remove**   Delete an inode and return its blocks to the free list.
* **stat**     Report the size of a given inode.
* **read**     Copy bytes from an inode into a host-side file or buffer.
* **write**    Copy bytes from a host-side file or buffer into an inode.

Attribution
-----------
Project specification, starter code, and diagrams were provided by  
**University of Notre Dame – CSE 30341**.  This repository contains my
independent re-implementation completed for portfolio purposes and is **not**
submitted for academic credit.

License
-------
The original framework is released under the University of Notre Dame licence;
all additional code written by me is released under the MIT License unless
otherwise noted.
```
