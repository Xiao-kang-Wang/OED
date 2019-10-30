### What is OPEX?

DeepPep, is a **protein identification** software which uses deep-convolutional neural network to predict the protein set from a proteomics mixture, given the sequence universe of possible proteins and a target peptide profile.

### Dependencies
* [mlegp](https://cran.r-project.org/web/packages/mlegp/index.html)

### Structure of this project

### Input data
Culutre condition: "Chlorexidine","Phenol","H2O2","Isopropanol","Bezalkonium_chloride","Ethanol","Glutaraldehyde","Percetic_acid","Sodium_hypochlorite","Povidone_iodine","Kanamycin","Rifampicin","Norfloxacin","Ampicillin".

Gene expression profile"thrA","thrB"
### Running
* Step1: generate a file that include many configurations to run OED.
  ```
  cd generate_setting
  Rscript expert_sampling.R
  ```
  After running the above commands, a file named ```expert_sampling.csv``` is generated in ```./out_data```. The ```expert_sampling.csv``` specifies the value for these hyper-parameters: random_seed, exploration frequency, adaptive , start size, add, dataset id, noise, iter_num, method. 

* Step2: Run the simulation on one setting.
```
cd code
bash run_one_setting.sh
```

Upon completion, a folder named ```expert_sample``` will be created in ```./out_data```. The folder has the same name as the Rscript used for generating configurations in Step 1. Inside the folder, ```expert_sample```, there are a folder for each sampling approach.





### Acknowledgement
This work was supported by an NSF award.
