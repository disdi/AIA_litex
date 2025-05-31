---
title: Roadmap
---

Roadmap
=======

 

## Implementation Roadmap

### Phase 1: Foundation

#### 1.1 Core Infrastructure
- [ ] Define AIA memory map regions in LiteX
- [ ] Create base classes for AIA components
- [ ] Implement CSR extensions for VexRiscv (Smaia)
- [ ] Setup interrupt routing infrastructure

#### 1.2 ACLINT Implementation
- [ ] Implement MTIMER device
- [ ] Implement MSWI device
- [ ] Ensure backward compatibility with existing CLINT
- [ ] Create device tree bindings

### Phase 2: APLIC Development

#### 2.1 Basic APLIC
- [ ] Implement APLIC register interface
- [ ] Support for up to 1023 interrupt sources
- [ ] Direct delivery mode implementation
- [ ] Basic interrupt routing logic

#### 2.2 Advanced APLIC Features
- [ ] MSI delivery mode support
- [ ] Hierarchical domain implementation
- [ ] Interrupt delegation between M/S modes
- [ ] Integration with system bus

### Phase 3: IMSIC Integration

#### 3.1 IMSIC Core
- [ ] Implement interrupt file structure
- [ ] MSI reception and recording logic
- [ ] CSR interface (mtopei, stopei)
- [ ] Interrupt priority handling

#### 3.2 IMSIC-APLIC Integration
- [ ] MSI forwarding from APLIC to IMSIC
- [ ] Unified interrupt routing
- [ ] Performance optimization
- [ ] Multi-core synchronization

### Phase 4: Software Support

#### 4.1 Bare-metal Support
- [ ] AIA initialization routines
- [ ] Interrupt handler templates
- [ ] Driver API for APLIC/IMSIC
- [ ] Example applications

#### 4.2 Linux Support
- [ ] Device tree bindings
- [ ] Linux interrupt controller drivers
- [ ] Integration with existing IRQ subsystem
- [ ] Performance benchmarking tools

### Phase 5: Verification & Testing

#### 5.1 Compliance Testing
- [ ] RISC-V AIA specification compliance
- [ ] Interrupt latency measurements
- [ ] Priority handling verification
- [ ] Multi-core stress testing

#### 5.2 System Integration
- [ ] Full SoC integration testing
- [ ] Peripheral interrupt testing
- [ ] Software compatibility validation
- [ ] Documentation completion

## Benefits Over CLIC

While CLIC offers excellent real-time capabilities, AIA provides:

1. **Better Scalability**: Designed for systems with thousands of cores
2. **MSI Support**: Native support for modern peripheral standards
3. **Virtualization**: Hardware support for interrupt virtualization
4. **Industry Alignment**: Broader ecosystem support and standardization
5. **Flexibility**: Modular design allows partial implementation


## Conclusion

Implementing AIA support in LiteX positions the framework at the forefront of RISC-V interrupt architecture evolution. This enhancement will enable LiteX-based SoCs to support modern peripherals, virtualization, and scale to larger multi-core systems while maintaining the framework's ease of use and flexibility.

The modular approach allows for incremental implementation, reducing risk while delivering value at each phase. With proper execution, LiteX will become the go-to platform for exploring and deploying advanced RISC-V interrupt architectures.