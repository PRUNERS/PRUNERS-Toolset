<img src="doc/images/pruners_logo.png" height="60%" width="60%" alt="PRUNERS logo" title="PRUNERS" align="middle" />

## OVERVIEW
Reproducibility is highly desirable for parallel applications, but as they are run on increasingly large and heterogeneous platforms, reproducibility of numerical results or code behaviors is becoming less and less obtainable. The same code can produce different results or occasional failures such as a crash on different systems or even across different runs on the same hardware. PRUNERS is a research and development project that aims at innovating scalable techniques to aid applications to obtain the reproducibility. Specifically, our strategy is to accomplish this by developing a multilevel analysis and control toolset called the PRUNERS Toolset, which combines static and dynamic analysis techniques to detect, control and eliminate targeted sources of non-determinism, as introduced through parallel programming libraries and APIs.

## COMPONENTS

### Archer

<img src="doc/images/archer_logo.png" hspace="1" vspace="1" height="25%" width="25%" alt="Archer Logo" title="Archer" align="left" />

Archer is a data race detector for OpenMP programs.

Archer combines static and dynamic techniques to identify data races in large OpenMP applications, leading to low runtime and memory overheads, while still offering high accuracy and precision. It builds on an open-source tools infrastructure including LLVM, ThreadSanitizer, and OMPT to provide portability.

More Information about Archer can be found [here](https://pruners.github.io/archer/).

### FLiT

<img src="doc/images/flit-small.png" hspace="1" vspace="1" height="10%" width="10%" alt="FLiT Logo" title="FLiT" align="left" />

Floating-point Litmus Tests is a test infrastructure for detecting varibility in floating-point code caused by variations in compiler code generation, hardware and execution environments.

FLiT works by building many versions of the test suite, using multiple C++ compilers, floating-point related settings (i.e. flags) and optimization levels. These tests are then executed on target platforms, where a representative ‘score’ is collected into a database, along with the other parameters relevant to the execution, such as host, compiler configuration and compiler vendor. In addition to the user-configured test output, we collect counts of each assembly opcode executed (currently, this works with Intel architectures only, using their PIN dynamic binary instrumentation tool).

After executing the suite and collecting the data, it is easy to see how results may diverge using only different compiler settings, etc. Also, the developer is able to understand how to configure their build environment for their target architecture(s) such that they can expect consistent floating-point computations.

More Information about FLiT can be found [here](https://pruners.github.io/flit/).

### NINJA

<img src="doc/images/NINJA_logo.png" hspace="1" vspace="1" height="25%" width="25%" alt="NINJA logo" title="NINJA" align="left" />

NINJA (Noise INJection Agent) is a smart network noise injector for quickly exposing unindended MPI message races. NINJA uses innovative network noise injection techniques to increase the chances of racy, incorrect MPI message matching within the target MPI application. NINJA has been shown to reproduce unsafe message races consistently within large production applications and can do this up to two orders of magnitude faster than the traditional testing approach (i.e., random noise injection).
More Information about NINJA can be found [here](https://pruners.github.io/ninja/).

### ReMPI
<img src="doc/images/rempi_logo.png" hspace="1" vspace="1" height="25%" width="25%" alt="ReMPI logo" title="ReMPI" align="left" />
ReMPI is a highly scalable scalable record-and-replay tool for MPI applications. ReMPI records the order of MPI message matching in one run and can deterministically replay it during subsequent runs. One of the supported modes uses Clock Delta Compression (CDC) for running at extreme-scale. CDC can reduce the record size down to the bare minimum, which allows ReMPI to keep record data on node-local storage, and drastically improve scalability versus writing to a shared file system.

More Information about ReMPI can be found [here](https://pruners.github.io/rempi/).

## INSTALLING THE PRUNERS 
The PRUNERS Toolset has been packaged in the [Spack](https://github.com/LLNL/spack) package manager for easy installation of the PRUNERS components and all of their dependent packages.

    git clone https://github.com/LLNL/spack.git
    cd spack
    ./bin/spack install archer
    ./bin/spack install pruners-ninja
    ./bin/spack install rempi

Alternatively, you may download any release of a component or clone any component from its git repo and manually install. Each component can be found by navigating the [PRUNERS github organization](https://github.com/PRUNERS). Refer to the README file for installation instructions.

FLiT packaging in Spack is a work in progress. In the meantime, refer to [the FLiT Project](https://github.com/PRUNERS/FLiT) for manual installation instructions.

## LICENSE

Each individual PRUNERS tool is released under either the GNU Lesser General Public License (LGPL) or the Berkeley Software Distribution (BSD) public license. Please refer to the LICENSE file included in each project for more details. 
