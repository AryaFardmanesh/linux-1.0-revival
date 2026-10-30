# Linux 1.0 Revival (`linux-1.0-revival`)

Resurrecting and modernizing the original **Linux 1.0.0 (March 1994)** codebase to compile, link, and boot using a strictly modern, minimal x86 toolchain.

---

## 🎯 Objectives
- **Clean Toolchain**: Modernize legacy assembly and 32-bit freestanding C for current GCC and modern NASM.
- **Modern Build System**: Replace archaic make rules with a modular, maintainable GNU Makefile.
- **Native Emulation**: Out-of-the-box support for execution inside modern QEMU environments.
- **Systems Playground**: Serve as a bare-metal testbed for low-level experimentation, custom boot stages, and lightweight C libraries.

---

## 🛠️ Toolchain & Requirements

To build and run the modernized kernel on an x86_64 Linux machine, only three core toolsets are required:

```bash
# Ubuntu / Debian
sudo apt update
sudo apt install -y build-essential gcc gcc-multilib nasm qemu-system-x86
```

- **GCC** (with 32-bit support via multilib)
- **NASM** (for modern x86 boot and assembly subroutines)
- **QEMU** (`qemu-system-i386` for verification and hardware testing)

---

## 🚀 Build & Run

### 1. Build the Kernel
```bash
make
```

### 2. Launch in QEMU
```bash
make run
```
*Or manually via:*
```bash
qemu-system-i386 -kernel build/zImage -serial stdio
```

---

## 📂 Repository Structure
```text
linux-1.0-revival/
├── docs/             # All repository documentation
│   └── historical/   # Historical documentation
├── boot/             # Real-mode startup & setup stages (modernized via NASM)
├── init/             # High-level kernel entry point (main.c)
├── kernel/           # Task scheduling, IRQ dispatch, signal handling
├── mm/               # x86 paging & physical memory allocator
├── fs/               # Virtual Filesystem Layer (VFS), ext2, minix
├── drivers/          # Device drivers (char, block, net)
├── Makefile          # Root build orchestration
└── LICENSE           # GNU General Public License v2
```

---

## 📜 License & Acknowledgments
- **Modernization & Porting:** Maintained by **Arya Fardmanesh**.
- **Original Codebase:** Copyright (C) 1991–1994 Linus Torvalds and original contributors.
- **Historical Attribution:** Original developer credits are preserved in [`docs/historical/CREDITS`](docs/historical/CREDITS).
- Licensed under the terms of the **GNU General Public License v2 (GPLv2)**. See [LICENSE](LICENSE).
