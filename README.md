# vmlinux

Pre-generated `vmlinux.h` for eBPF development (kprobe, XDP, TC).

## Kernel Version

Generated from kernel **~6.1**. Sourced from [cilium/pwru](https://github.com/cilium/pwru).

| File | Architecture | Size |
|---|---|---|
| `vmlinux-x86.h` | x86_64 / amd64 | 2.5 MB |
| `vmlinux-arm64.h` | aarch64 / arm64 | 2.1 MB |
| `vmlinux-loongarch.h` | loongarch64 | 2.7 MB |
| `vmlinux-riscv.h` | riscv64 | 2.4 MB |

## Usage

### As git submodule

```bash
git submodule add https://github.com/<YOU>/vmlinux.git bpf/headers
```

### Architecture selection

This repo does NOT provide an architecture selector. Each project implements its own:

```c
#if defined(__TARGET_ARCH_x86)
#include "headers/vmlinux-x86.h"
#elif defined(__TARGET_ARCH_arm64)
#include "headers/vmlinux-arm64.h"
#elif defined(__TARGET_ARCH_loongarch)
#include "headers/vmlinux-loongarch.h"
#elif defined(__TARGET_ARCH_riscv)
#include "headers/vmlinux-riscv.h"
#else
#error "Unsupported architecture, define __TARGET_ARCH_xxx"
#endif
```

### Clone with submodule

```bash
git clone --recurse-submodules https://github.com/<YOU>/your-project.git
```

Or init after clone:

```bash
git submodule update --init
```
