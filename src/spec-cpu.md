## SPEC-CPU cheat sheet

### SHORT DESCRIPTION (SPEC-CPU 2017)
The SPEC CPU® 2017 benchmark package contains SPEC's next-generation, industry-standardized, CPU intensive suites for measuring and comparing compute intensive performance, stressing a system's processor, memory subsystem and compiler.

---
#### Build a single benchmark
```bash 
cd $SPEC
source shrc
cp config/Example-gcc-x86.cfg mycfg.cfg
runcpu --config mycfg --action=build 505.mcf_r
```

---

#### Build and run a single benchmark (no-reportable)
```bash 
cd $SPEC
source shrc
cp config/Example-gcc-x86.cfg mycfg.cfg
runcpu --config mycfg --size test --copies 1 --noreportable --iterations 1 505.mcf_r
```
---

#### Clean *build* and *exe* files
```bash
cd $SPEC
source shrc
runcpu --action clean --config myconfig 505.mcf_r
```

---

#### Buld a single benchmark without runcpu
```bash
cd $SPEC
source shrc
runcpu --fake --loose --size test --tune base --config myconfig 505.mcf_r
```

---

#### RISC-V benchmarks

Configuration file: [Example-gcc-linux-gcc.cfg](https://www.spec.org/cpu2017/Docs/Example-gcc-linux-riscv.cfg)

---
