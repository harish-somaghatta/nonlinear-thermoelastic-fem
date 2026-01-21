# Nonlinear Thermoelastic FEM (2D) — MATLAB Implementation

This project implements a **fully coupled nonlinear thermoelastic finite element solver (2D)** using a **Newton–Raphson** iterative scheme.  
It includes temperature-dependent material behavior and coupling between mechanical deformation and heat transfer.

Verification is documented in the included report and compared against analytical checks and Abaqus simulations.

## Repository Structure

```text
.
├── src/                       # MATLAB solver + routines
│   ├── mainCouplefem.m         # Main script
│   ├── elementMechfem.m        # Mechanical element routine
│   ├── elementThermalfem.m     # Thermal element routine
│   ├── elementMechThermfem.m   # Coupled thermo-mechanical element routine
│   ├── materialMechfem.m       # Mechanical material model
│   ├── materialThermalfem.m    # Thermal material model
│   ├── extractDataInpFile.m    # Reads Abaqus-style .inp mesh files
│   ├── shapefunctions.m        # Shape functions for quad elements
│   ├── gaussPointsWeights.m    # Gauss quadrature points/weights
│   ├── Bmatrix.m               # Strain-displacement B-matrix
│   ├── recoveryStressStrain.m  # Stress/strain recovery (postprocessing)
│   ├── plotMesh.m              # Mesh visualization
│   ├── numericalTesting.m      # Verification / debugging tests
│   ├── temperatureVisualization.m # Temperature field plots
│   ├── square100Element.inp    # Example mesh (100 elements)
│   └── squareCenterHoleFineMesh.inp # Example mesh (center hole)
├── README.md
└── Report_NFEM.pdf             # Full report (theory + validation)
```
## Features
 - Fully coupled thermomechanical formulation (2D)
 - Nonlinear Newton–Raphson solution procedure
 - Implicit time integration (steady-state / transient support)
 - Quadrilateral elements (shape functions + Jacobian mapping)
 - Gauss quadrature for numerical integration
 - Validation with analytical checks and Abaqus comparisons (see report)

## Requirements
- MATLAB (required)
- Gmsh (optional — mesh generation)
- Abaqus (optional — verification)

## How to Run
1. Open MATLAB
2. Go to the repository folder
3. Navigate into src/
4. Run the main script (example):
```matlab
% inside src/
mainCouplefem
```
Note: Refer to [Report_NFEM.pdf](Report_NFEM.pdf) for test cases, configurations, and validation plots.

## Documentation
 - Full explanation of the governing equations, implementation details, and verification:
    - **[Report_NFEM.pdf](Report_NFEM.pdf)**








