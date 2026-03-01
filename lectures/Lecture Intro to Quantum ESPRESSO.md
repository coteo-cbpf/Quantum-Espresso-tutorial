
## Lecture: Introduction to Quantum ESPRESSO

### Quantum ESPRESSO: Main Features and Parameters
*An integrated suite for electronic-structure calculations and materials modeling at the nanoscale*


---

### What is Quantum ESPRESSO?
- **QE** is an integrated suite of open-source computer codes for electronic-structure calculations and materials modeling .
- It is based on **Density Functional Theory (DFT)**, using a basis of **plane waves** and the **pseudopotential** method .
- The name stands for **"opEn Source Package for Research in Electronic Structure, Simulation, and Optimization"** .
- It is a major code in computational materials science, building on methodologies like Car-Parrinello molecular dynamics and Density-Functional Perturbation Theory .


###  Global Impact: A Community Standard
- **Unprecedented Citation Count:** The two main papers describing QE are among the most cited in computational physics.
    - The 2009 paper has over **27,000** citations .
    - The 2017 paper has over **7,600** citations .
    - These papers have been authored by over **25,000** unique scientists .
- **Massive User Base:** It is estimated that QE has over **40,000** users worldwide, making it the most used open-source software in its field .
- **Active Community:** The users' mailing list exchanges over **2,000** messages per year, demonstrating a vibrant and supportive community .



### The Core Methodology
- **Density-Functional Theory (DFT):** The fundamental framework for calculating the electronic ground state of a system.
- **Plane Waves (PW):** A complete and unbiased basis set used to expand the Kohn-Sham orbitals. This is ideal for periodic systems like crystals.
- **Pseudopotentials:** These replace the strong ionic potential and core electrons with a weaker effective potential acting on the valence electrons. This significantly reduces the computational cost and the size of the plane-wave basis set required . QE supports:
    - Norm-conserving pseudopotentials
    - Ultrasoft (US) pseudopotentials (Vanderbilt type)
    - Projector Augmented Wave (PAW) method 

---

### Main Features: Ground-State & Structure
Quantum ESPRESSO is modular. The core components handle a wide variety of calculations.

- **Ground-State Calculations (PWscf module):**
    - Self-consistent total energies, forces, stresses, and Kohn-Sham orbitals .
    - Supports collinear and noncollinear magnetism, including spin-orbit coupling .
    - Berry phase calculations for polarization .
- **Structure Optimization & Dynamics:**
    - **Structural optimization** (BFGS, damped dynamics) to find stable atomic configurations .
    - **Born-Oppenheimer Molecular Dynamics (BOMD)** and **Car-Parrinello Molecular Dynamics (CPMD)** .
    - **Nudged Elastic Band (NEB)** method for finding reaction pathways and transition states .

### Main Features: Advanced Functionals & Methods
QE goes beyond standard DFT approximations.

- **Exchange-Correlation Functionals:** A vast library from LDA and GGA (PBE, PW91) to meta-GGA, hybrid functionals (PBE0, B3LYP, HSE), and exact exchange (HF) .
- **Van der Waals Corrections:** Includes Grimme's DFT-D2/D3, Tkatchenko-Scheffler, and non-local vdW-DF functionals .
- **Strongly Correlated Systems:** Implements DFT+U and DFT+U+V (Hubbard corrections) .
- **Electrochemistry:** Specialized boundary conditions like the Effective Screening Medium (ESM) method for surfaces and interfaces in solution .

### Main Features: Response Properties & Spectroscopies
A key strength of QE is its ability to calculate response properties using **Density-Functional Perturbation Theory (DFPT)** .

- **Vibrational Properties (PHonon module):**
    - Phonon frequencies and eigenvectors at any wavevector .
    - Full phonon dispersions and interatomic force constants.
    - Infrared and Raman cross-sections .
- **Electron-Phonon Coupling (EPW module):** Calculates electron-phonon coefficients and related properties (e.g., superconductivity) .
- **Spectroscopic Properties:**
    - **TDDFPT** (TurboTDDFT) for optical absorption and Electron Energy Loss Spectroscopy (EELS) .
    - **X-ray Absorption Spectra (Xspectra module)** .
    - **NMR chemical shifts (GIPAW)** .

---

###  Key Input Parameters: The Control Block
The input for the main `pw.x` executable is organized into namelists. Let's look at the most important ones.

- **&CONTROL:** Directs the type of calculation and output.
    - `calculation = 'scf'` : Self-consistent field (ground state energy).
    - `calculation = 'relax'` : Structural optimization (ion relaxation).
    - `calculation = 'vc-relax'` : Variable-cell relaxation (optimize cell shape/volume).
    - `calculation = 'nscf'` : Non-self-consistent (for bands, DOS).
    - `restart_mode`: Controls whether to start fresh (`'from_scratch'`) or restart (`'restart'`) .
    - `tstress` / `tprnfor`: Logical flags to calculate stresses and forces .
    - `pseudo_dir`: Directory containing the pseudopotential files .
    - `outdir` / `wfcdir`: Directories for temporary and wavefunction files .

###  Key Input Parameters: The System & Electrons Blocks
- **&SYSTEM:** Defines the physical system and computational parameters.
    - `ibrav`: Bravais lattice index (e.g., `ibrav=1` for cubic, `ibrav=0` for no symmetry) .
    - `celldm(i)`: Crystalline lattice constants (in Bohr or Alat) .
    - `nat` / `ntyp`: Number of atoms and number of types of atoms .
    - **`ecutwfc`**: The most critical parameter! The kinetic energy cutoff (in Ry) for the plane-wave basis set. **Must be converged** .
    - `ecutrho`: Cutoff for the charge density and potential (usually 4-12 times `ecutwfc`) .
    - `occupations`: How to occupy states (`'smearing'` for metals, `'fixed'` for insulators) .
    - `tot_charge`: Total charge of the system .

- **&ELECTRONS:** Controls the SCF convergence.
    - `conv_thr`: Convergence threshold for the SCF energy (in Ry). A typical value might be `1.0d-8` to `1.0d-10` for tight convergence .
    - `mixing_beta`: Mixing factor for charge density in the SCF cycle (default 0.7). Lower values can help difficult cases converge .
    - `electron_maxstep`: Maximum number of SCF iterations .
    - `diagonalization`: Algorithm for solving the eigenvalue problem (e.g., `'davidson'`) .

###  Key Input Parameters: I/O & K-Points
- **ATOMIC_SPECIES:** Links each atomic type to a pseudopotential file and its atomic mass .
    ```
    ATOMIC_SPECIES
    Sr  87.62  Sr.pbe.UPF
    ```
- **ATOMIC_POSITIONS:** Lists the coordinates of each atom, using the specified format (`crystal`, `angstrom`, `bohr`) .
- **K_POINTS:** Defines the sampling of the Brillouin zone.
    - `automatic` : Generates a Monkhorst-Pack grid (e.g., `K_POINTS automatic 6 6 6 1 1 1`) .
    - `gamma` : Uses the faster Gamma-point only routines .
    - A higher k-point density is required for metals and insulators with small band gaps. **Must be converged**.

---

###  Parallelism and Performance
QE is designed for high-performance computing (HPC) and scales well on parallel architectures .

- **Hybrid Parallelization:** Employs a mixed MPI and OpenMP paradigm .
- **Multiple Parallelization Levels:**
    - **Pool parallelism (`-npool`):** Distributes **k-points** among MPI groups. This is the most efficient first step .
    - **Band / Linear Algebra:** Distributes the calculation over **bands**.
    - **Plane-Wave / FFT:** Distributes the 3D FFT grid over processors (requires careful tuning) .
- **GPU Acceleration:** Recent versions support offloading computations to NVIDIA and AMD GPUs for significantly faster calculations .
- **Command-line Options:** Parallelism is controlled at runtime when you launch the executable, e.g.:
    `mpirun -np 128 pw.x -npool 8 -in input.in > output.out`

###  Summary & Resources
- **Quantum ESPRESSO** is a powerful, versatile, and community-driven open-source software package for quantum materials modeling.
- Its core strength lies in its comprehensive implementation of DFT, DFPT, and many advanced methodologies .
- A successful calculation requires careful selection of **pseudopotentials**, and convergence testing of key parameters like **`ecutwfc`** and the **k-point grid**.
- Its efficient parallelization allows it to run on systems ranging from workstations to the largest supercomputers .

- **Resources:**
    - Official Website: [www.quantum-espresso.org](https://www.quantum-espresso.org/) 
    - Key Papers: Giannozzi et al. (2009, 2017) 
    - Documentation & Tutorials: Available on the official site and in the code repository.
