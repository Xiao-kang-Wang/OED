### What is OPEX?

DeepPep, is a **protein identification** software which uses deep-convolutional neural network to predict the protein set from a proteomics mixture, given the sequence universe of possible proteins and a target peptide profile.

### Dependencies
* [mlegp](https://cran.r-project.org/web/packages/mlegp/index.html)

### Structure of this project

### Input data
Culutre condition: "Chlorexidine","Phenol","H2O2","Isopropanol","Bezalkonium_chloride","Ethanol","Glutaraldehyde","Percetic_acid","Sodium_hypochlorite","Povidone_iodine","Kanamycin","Rifampicin","Norfloxacin","Ampicillin".

Gene expression profile"thrA","thrB"
### Running
* Step1: generate configuration files to run OED.
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

Upon completion, ```pred.csv``` will contain the predicted protein identification probabilities.

### Benchmark Datasets
There are [7 example datasets](https://github.com/ameenetemady/DeepPep/tree/master/data) (used for benchmarking in the paper). Each dataset is generated from MS/MS raw files using TPP pipeline.

### Citation
 M. Kim, A. Eetemadi, and I. Tagkopoulos, “DeepPep: deep proteome inference from peptide profiling”, PLoS Computational Biology (2017) *under review*

### Licence
See the [LICENSE](./LICENSE) file for license rights and limitations (Apache2.0).

### Acknowledgement
This work was supported by a grant from Mars, Inc. and NSF award 1516695.
