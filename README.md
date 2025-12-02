# openmc-fusionblanket
Characterising fusion blanket

## Folder Structure

- `startup/`  
  Contains simple start up script to activate micromamba + openMC + data.
  
- `flibe_test/`  
  Transport + (optional) depletion test using FLiBe (LiF–BeF₂).

- `lipbba_test/`  
  Transport + (optional) depletion test using Li–Pb–Ba ternary alloy based on Jolodosky paper shared by Prof Fratoni. Currently only set at 5 batches. 

- `analyze_activation/`  
  Contains script to analyze material activation from the depletion results.

- `data/`  
  Nuclear cross section libraries (e.g., ENDF/B-VII.0 MCNP library).  
  Contains `cross_sections.xml` and related data.

- `scratch/`  
  Output files from OpenMC runs (statepoints, tallies, etc.).  
  Safe to delete if you want a clean restart.

---

## Notes

Inside Codespaces, OpenMC is installed using micromamba:

- micromamba
- openmc (with DAGMC + MPI support)
- python 3.11

---

## Instructions

- Before opening a new codespaces/terminal, run startup script: 
`source /workspaces/openmc-fusionblanket/start_openmc.sh/`  
This script includes all the commands to reconnect everything which includes:
1) Enable micromamba
2) Activate openMC 
3) Setting the nuclear data path (ENDF cross section data)
4) Setting the depletion chain 

- To run depletion tests for each blanket type:
1) Go to script folder: `cd /workspaces/openmc-fusionblanket/(ALLOY NAME)_test/`  
2) Run the script: `python (ALLOY NAME)_activation_test.py/`

- To extract activities from depletion results, run analysis script:
`python /workspaces/openmc-fusionblanket/analyze_activation/activation_to_ci_per_m3.py/`
Update line 19 and 20 based on blanket type.

- To return to main project folder:
cd /workspaces/openmc-fusionblanket

- To make new folder:
mkdir -p (FOLDER NAME)



