# README.md

## Project Overview

The purpose of this study is to provide an innovative quantitative analysis of ultra-close fault dynamic rupture and its impact on roadway stability, specifically focusing on the effects of wave reflection and amplification during deep excavation. Additionally, by making our computational models and codes openly accessible, we aim to advance future research in fault-induced seismic risk assessment and improve design strategies for seismic resilience in underground environments.

Software name: PyLith (Version 2.2.2)
The Computational Infrastructure for Geodynamics (CIG) at [geodynamics.org](https://geodynamics.org) is providing this source code free of charge, with the hope that it will advance your geophysics research.

Licence: PyLith is an open-source software licensed under the GNU General Public License (GPL) version 2.0.

<!-- This project focuses on finite element analysis of geological models, particularly simulating the complex processes of crustal deformation. With the help of PyLith software, we have successfully constructed a fine mesh model and executed a series of simulation steps to explore the dynamic behavior of the roadway excavation induced rupture. Through this README, you will be able to understand the model configuration and processing methods. -->

## Project File Organization

- `mesh.exo`: Contains the completed fine mesh model file.
- `roadway-excavation-dynamic-rupture.cfg`: PyLith configuration file for precise control of simulation startup and execution.
- `fault_slipweakening.spatialdb`: Defines key parameters used in the simulation, such as μs, μd, Dc.
- `fault_tractions.spatialdb`: Defines the traction applied to the fault surface.

## Analysis Parameters

Our current analysis relies on the mechanical parameters specified in Tables 1 and Tables 2. Utilizing PyLith 2.2.2, we were able to accurately simulate fault dynamic rupture and seismic wave propagation induced by roadway excavation.

## Tables 1: Fault parameters, roadway design, and stress conditions

| Description | Value |  
| --- | --- |  
| Fault dip angle, φ (°) | 75 |  
| Vertical stress, σV (MPa) | Self-gravity |  
| Horizontal stress ratio, σh/σV | 0.5 |  
| Roadway height, RH (m) | 3.6 |  
| Roadway width, RW (m) | 5.5 |  
| Coal seam thickness above roadway (m) | 1.1 |  
| Coal seam thickness below roadway (m) | 0.3 |  
| Mining depth, h, (m) | 500 |  
| Static friction coefficient, μs | 0.47 |  
| Dynamic friction coefficient, μd | 0.27 |  
| Critical slip distance, Dc (mm) | 1 |  
| Fault-roadway distance, D (m) | 3 |

## Tables 2: Stratigraphic Layers Properties and Wave Velocities

| No. | Lithology | T (m) | ρ (kg/m³) | ν | G (GPa) | K (GPa) | Vs (m/s) | Vp (m/s) |  
| --- | --- | --- | --- | --- | --- | --- | --- | --- |  
| L1 | Sandstone | 60 | 2500 | 0.25 | 4.8 | 8 | 1385.6 | 2400 |  
| L2 | Siltstone | 5 | 2400 | 0.25 | 3.2 | 5.3 | 1154.7 | 2000 |  
| L3 | Coal | 5 | 1300 | 0.25 | 0.8 | 1.3 | 784.5 | 1358.7 |  
| L4 | Sandstone | 30 | 2500 | 0.25 | 4.8 | 8 | 1385.6 | 2400 |  
  
**Note**: T: Thickness; ρ: Density; ν: Poisson’s ratio; G: Shear Modulus; K: Bulk modulus; Vs: Shear wave velocity; Vp: Compressional wave velocity.

## Running Guide

1. Refer to the official PyLith documentation to ensure the correct installation of PyLith version 2.2.2.
2. In the project root directory, start the simulation process with the following command:

```bash
cd /YOUR_PYLITH_PATH/pylith
source setup.sh

cd /YOUR_MODEL_PATH
pylith roadway-excavation-dynamic-rupture.cfg
```

After the simulation is complete, all results will be output to the `output` folder.

## Result Output and Viewing

After the simulation ends, you can find the following `.xmf` formatted result files in the `output` folder:

- `fault_traction.xmf`
- `model-all-disp.xmf`
- `material-h3.xmf`

These files record various data during the simulation process in detail, and you can use software like ParaView for viewing and analysis.

### Result Viewing Method:

- Open the ParaView software.
- Import `.xmf` files to view the simulation results.
- Utilize ParaView's rich toolset, such as slicing, isosurfacing, etc., to showcase the simulation data in all directions.
- If further data processing is required, you can use ParaView's Filter function to export the data in CSV format, providing convenience for subsequent in-depth analysis, such as calculating slip distribution or performing other statistical analyses.
