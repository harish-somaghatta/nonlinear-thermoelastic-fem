# Nonlinear Thermoelastic FEM (2D) — MATLAB Implementation

This project implements a **fully coupled nonlinear thermoelastic finite element solver (2D)** using a **Newton–Raphson** iterative scheme.  
 - It includes temperature-dependent material behavior and coupling between mechanical deformation and heat transfer.
 - Verification is documented in the included report and compared against analytical checks and Abaqus simulations.

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
 - Implicit time integration (steady-state / transient)
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
## Configurations

You can customize the analysis by modifying parameters inside `src/mainCouplefem.m`.

### Load Case Selection
```matlab
LoadCase = 5; % Choose from 5, 6, or 7 for different thermal loads
```
### Temperature-Dependent Material Properties
```matlab
temperatureDependent = 'yes'; % Set 'yes' for temperature-dependent properties
```
### Steady-State vs Transient Analysis
```matlab
steadyState = 'yes'; % Set 'no' for transient analysis
```
### Mesh Selection
```matlab
readFile = fopen('square100Element.inp', 'r');
```
## Testing and Validation
1. **Patch Test**
```matlab
testCase = 3;
eigenValueTest = 'no';
numericalTesting = 'no';
temperatureDependent = 'no';
steadyState = 'yes';
```
2. **Comparison with Analytical Solution**
```matlab
testCase = 1; % also supports 2 or 4 (see report)
eigenValueTest = 'no';
numericalTesting = 'no';
temperatureDependent = 'no';
steadyState = 'yes';
```
3. **Numerical Testing**
```matlab
testCase = 1;
eigenValueTest = 'no';
numericalTesting = 'yes';
temperatureDependent = 'no';
steadyState = 'yes';
```
4. **Eigenvalue Test**
```matlab
testCase = 1;
eigenValueTest = 'yes';
numericalTesting = 'no';
temperatureDependent = 'no';
steadyState = 'yes';
```

## Results
 - Displacement magnitude (u)
 - Temperature distribution (T)

## Documentation
 - Full explanation of the governing equations, implementation details, and verification:
    - **[Report_NFEM.pdf](Report_NFEM.pdf)**








