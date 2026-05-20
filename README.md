# Polarizability calculations for Rado's group

# Install 
You will need to install miniconda (lightweight version of anaconda):
https://www.anaconda.com/docs/getting-started/miniconda/install/overview

On windows just open the conda prompt in linux open the terminal.
Then navigate to the directory
```bash 
cd <windows or unix path of the github repo>
```

If you have trouble just ask the AI of your choice explaining the errors you encounter.

```bash
# At the top-level directory of the repo
conda env update -f install/psi4_rado-tuto.yaml
```

# How to run psi4
Open your unix terminal (subshell on windows) or you anaconda on windows:
```bash
cd minimal_script/run_lr/
conda activate psi4_rado-tuto
psi4 POLARIZ-LR_HF_cc-pvdz_CO2.psi4inp
```
This is just a test and if no error occurs it was successful. But you can run any other file by just navigating to the right directory with ```cd``` and running
the corresponding ```.psi4inp``` file.


# Production 
The scripts can be found under ```production_scripts```. 
The optimization is set to use MP2/cc-pvtz (notation
<method>/<basis-set>). The properties use PBE0/d-aug-cc-pvtz (this should give reasonable properties).
If better accuracy is required we may think about changing the method later on.

## Geometry Optimization
You need to get a starting geometry (e.g. experimental structure from NIST or example from IQmol project), e.g.:
* https://cccbdb.nist.gov/expgeom1x.asp
* https://github.com/nutjunkie/IQmol/blob/master/share/fragments/Molecules/Aromatics/Benzene.xyz
Ideally, you check that the geometry is what you expect by putting it into .xyz file format and open it with a molecule viewer (I use jmol, but for windows there are likely nicer ones).

Then replace the geometry in the file (I put CO2 as example, the formats should be in .xyz file format, it's ANGSTROM
not BOHR! units). Only do closed shell molecules for now! Just run the file then:
```bash
   psi4 OPT_<...>.psi4inp
```
After that there should be a new .xyz file in the directory. That is the optimized geometry! You should check the
reasonability of this structure through the molecule viewer like before.

## Properties Calculations
Take this optimized geometry and put it into the properties file and run:
```bash
   psi4 PROPERTIES_<...>.psi4inp
```
Find a ```properties.yaml``` file that can be used to further process the results (this file is in atomic units
[electrons and Bohr!]).

# Follow up for May 20th
Bruno: 
- [x] provide production script for property computation (dump everything together with polarizabilities into yaml file)
- [x] provide production script for optimization 

Rado's group: 
- [ ] see how to install git and subshell (using linux). 
- [ ] Follow production procedure (start with smallest compounds, e.g. Argon)
- [ ] Think were to run more computationally demanding jobs
- [ ] Ask rado if he needs dipole-quadrupole polarizabilities
