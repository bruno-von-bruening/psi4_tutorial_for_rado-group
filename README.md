# Polarizability calculations for Rado's group

# Install 
You will need to install miniconda (lightweight version of anaconda):
https://www.anaconda.com/docs/getting-started/miniconda/install/overview

If you have trouble just ask the AI of your choice explaining the errors you encounter.

```bash
# At the top-level directory of the repo
conda env update -f install/psi4_rado-tuto.yaml
```

# Test
```bash
conda activate psi4_rado-tuto
cd minimal_script/run_lr/
psi4 POLARIZ-LR_HF_cc-pvdz_CO2.psi4inp
```
If no error occurs you should be good to go.

