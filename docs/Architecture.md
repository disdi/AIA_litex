---
title: Architecture
---

# AIA LiteX SoC Framework Architecture

## Core Components Integration

We propose implementing the following AIA components in LiteX:

1. **IMSIC (Incoming MSI Controller)**
   - One IMSIC per VexRiscv core
   - Support for machine and supervisor-level interrupt files
   - Initial implementation without guest interrupt files

2. **APLIC (Advanced Platform-Level Interrupt Controller)**
   - Centralized interrupt routing for wired interrupts
   - Support for both direct delivery and MSI forwarding modes
   - Hierarchical domain support for M-mode and S-mode

3. **ACLINT Compatibility**
   - Maintain backward compatibility with existing timer and software interrupt mechanisms
   - Implement as separate MTIMER and MSWI devices per AIA specification

### System Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  VexRiscv   │     │  VexRiscv   │     │  VexRiscv   │
│    Core 0   │     │    Core 1   │     │    Core N   │
└──────┬──────┘     └──────┬──────┘     └──────┬──────┘
       │                   │                   │
    ┌──┴──┐             ┌──┴──┐             ┌──┴──┐
    │IMSIC│             │IMSIC│             │IMSIC│
    │  0  │             │  1  │             │  N  │
    └──┬──┘             └──┬──┘             └──┬──┘
       │                   │                   │
       └───────────────────┴───────────────────┘
                          │
                    ┌─────┴─────┐
                    │   APLIC   │
                    │           │
                    └─────┬─────┘
                          │
                ┌─────────┴─────────┐
                │ Peripheral Devices│
                └───────────────────┘
```




## Software Architecture

### Driver Stack Overview

```
┌─────────────────────────┐
│    User Applications    │
├─────────────────────────┤
│     Linux Kernel        │
├─────────────────────────┤
│   IRQ Domain Subsystem  │
├─────────────────────────┤
│  AIA Driver Framework   │
├──────────┬──────────────┤
│  APLIC   │    IMSIC     │
│  Driver  │    Driver    │
└──────────┴──────────────┘
```

### Key Software Components

1. **APLIC Driver**
   - Device initialization
   - Interrupt routing configuration
   - Domain management
   - MSI address generation

2. **IMSIC Driver**
   - Interrupt file management
   - CSR access abstraction
   - Priority handling
   - Vector table management

3. **Integration Layer**
   - IRQ domain mapping
   - Device tree parsing
   - Legacy compatibility
   - Performance monitoring

---
