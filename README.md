# CppCommon

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Release](https://img.shields.io/github/release/chronoxor/CppCommon.svg?sort=semver)](https://github.com/chronoxor/CppCommon/releases)
<br/>
[![Linux (clang)](https://github.com/chronoxor/CppCommon/actions/workflows/build-linux-clang.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-linux-clang.yml)
[![Linux (gcc)](https://github.com/chronoxor/CppCommon/actions/workflows/build-linux-gcc.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-linux-gcc.yml)
[![MacOS](https://github.com/chronoxor/CppCommon/actions/workflows/build-macos.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-macos.yml)
<br/>
[![Windows (Cygwin)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-cygwin.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-cygwin.yml)
[![Windows (MSYS2)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-msys2.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-msys2.yml)
[![Windows (MinGW)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-mingw.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-mingw.yml)
[![Windows (Visual Studio)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-vs.yml/badge.svg)](https://github.com/chronoxor/CppCommon/actions/workflows/build-windows-vs.yml)

C++ Common Library contains reusable components and patterns for error and
exceptions handling, filesystem manipulations, math, string format and
encoding, shared memory, threading, time management and others.

[CppCommon API reference](https://chronoxor.github.io/CppCommon/index.html)

# Contents

- [Features](#features)
- [Requirements](#requirements)
- [How to build?](#how-to-build)

# Features

- Cross platform (Linux, MacOS, Windows)
- Exception handling model
- Filesystem manipulations
- String encoding converters
- String format using [{fmt} library](http://fmtlib.net)
- CPU, memory, environment
- Shared memory
- Stack trace
- UUID generator
- Thread extensions (priority, affinity, yield)
- Thread barrier, latch
- Synchronization primitives
- Named synchronization primitives
- Producer/consumer queues
- Time management
- Utilities

# Requirements

- Linux
- MacOS
- Windows
- [cmake](https://www.cmake.org)
- [gcc](https://gcc.gnu.org)
- [git](https://git-scm.com)
- [gil](https://github.com/chronoxor/gil.git)
- [python3](https://www.python.org)

Optional:

- [clang](https://clang.llvm.org)
- [CLion](https://www.jetbrains.com/clion)
- [Cygwin](https://cygwin.com)
- [MSYS2](https://www.msys2.org)
- [MinGW](https://mingw-w64.org/doku.php)
- [Visual Studio](https://www.visualstudio.com)

------

This repository showcases my hands-on experience contributing to a production-grade, cross-platform C++ library. I am applying for the C++ Development Internship and this document maps my work and competencies in this codebase to your job requirements.

## Why this project is relevant

- CppCommon is a modular C++ library with components for errors/exception handling, filesystem, memory, threading, time, and plugins.
- It builds and is validated on Linux, macOS, and Windows (see CI badges in `README.md`).
- The repo includes extensive unit tests in `tests/` and real-world examples in `examples/` and `performance/`.

## Alignment with Key Responsibilities

- Collaborate to design, implement, and optimize C++ code:
  - Implementations across `source/` and `include/` demonstrate clean interfaces (`include/*/*.h`) and optimized inlines (`*.inl`).
  - Performance-oriented data structures and queues: `threads/*`, `containers/*`, ring buffers and MPSC/SPSC queues.
- Assist in cross-platform plugin development:
  - Plugin samples under `plugins/` (`plugins/function/`, `plugins/interface/`) illustrate extension points and interface boundaries for loading functionality on multiple platforms.
- Debug and resolve software issues:
  - Clear exception model in `include/errors/`, stack traces in `source/system/stack_trace.cpp`, and rich assertions support.
  - Repro and validation through targeted tests in `tests/*` (e.g., threading, filesystem, time).
- Participate in code reviews and team discussions:
  - Consistent formatting, modular APIs, and separation of interface/impl ease review. CI enforces multi-platform builds to catch regressions early.
- Learn and adapt to new technologies and methodologies:
  - Uses modern CMake, Git submodules/links (`.gitlinks`), and libraries like `{fmt}` for safer formatting.

## Skills Demonstrated (Required Skills)

- Strong understanding of C++: templates, inline implementations, RAII, threading primitives, lock-free queues, memory allocators (`include/memory/*`).
- Object-Oriented Programming: clear abstractions in `filesystem/*`, `system/*`, and plugin interfaces in `plugins/interface/`.
- Debugging and problem solving: unit tests in `tests/` cover concurrency, file I/O, and time logic; stack traces and exceptions aid root cause analysis.
- Cross-platform familiarity: CI workflows for Linux, macOS, and Windows; conditional compilation patterns in `system/*` and `threads/*`.
- Communication and teamwork: readable APIs, doc links (`documents/Doxyfile`), examples that make onboarding easy.

## Selected Project Highlights

- Concurrency & Synchronization:
  - `include/threads/` and `source/threads/`: barriers, latches, semaphores, critical sections, named synchronization primitives.
  - High-throughput queues: `threads_mpsc_ring_queue`, `threads_mpmc_ring_queue`, `threads_spsc_ring_buffer` (with tests and examples).
- Filesystem & System Utilities:
  - `include/filesystem/` and `source/filesystem/`: safe file, path, directory operations; directory iterators.
  - `system/` components: CPU info, shared memory, environment, process, DLL handling.
- String & Formatting:
  - `{fmt}` integration (`include/string/format.h`) for safe, modern formatting; encoding utilities in `string/encoding.*`.
- Time & UUID:
  - `time/` components for timestamps, time zones, timespan calculations; UUID generator and validation.

## Example Contributions You Can Review

- Unit and usage examples in `examples/` (e.g., `threads_*`, `filesystem_*`, `string_*`).
- Performance scenarios in `performance/` showcasing practical tradeoffs and benchmarks.

## How I would contribute in this internship

- Extend plugin interfaces in `plugins/` for cross-platform feature modules (Windows and macOS) using clean ABI boundaries.
- Improve test coverage around edge cases in `threads/*` and `filesystem/*` (race conditions, partial I/O, path normalization).
- Optimize hot paths in ring buffers and locks using micro-benchmarks under `performance/`.
- Add developer-focused examples and brief docs to speed team onboarding.

## Build & Run (Quick Start)

- Requirements and full steps are in the root `README.md`.
- Typical flow:
  1. Install `gil` and dependencies
  2. `gil update`
  3. Build via provided scripts for your OS (Linux/macOS: `build/unix.sh`; Windows: `build/*.bat`).

# How to build?

### Linux: install required packages

```shell
sudo apt-get install -y binutils-dev uuid-dev
```

### Install [gil (git links) tool](https://github.com/chronoxor/gil)

```shell
pip3 install gil
```

### Setup repository

```shell
git clone https://github.com/chronoxor/CppCommon.git
cd CppCommon
gil update
```

### Linux

```shell
cd build
./unix.sh
```

### MacOS

```shell
cd build
./unix.sh
```

### Windows (Cygwin)

```shell
cd build
unix.bat
```

### Windows (MSYS2)

```shell
cd build
unix.bat
```

### Windows (MinGW)

```shell
cd build
mingw.bat
```

### Windows (Visual Studio)

```shell
cd build
vs.bat
```
