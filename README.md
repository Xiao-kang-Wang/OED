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

Upon completion, a folder named ```expert_sample``` will be created in ```./out_data```. The folder has the same name as the Rscript used for generating configurations in Step 1. Inside the folder, ```expert_sample```, there is a folder for each sampling approach.

The result is a csv file named by the configuration and has the order of each culture condition selected by expert sampling.

### Code architecture
In this dir, ```./code/workhorse```, there are seven R scripts as follows. In ```main.R```, an object of the ```Simulate``` class is defined according to a configuration determined by a command line argument. The defintion of the ```Simulate``` class is defined in ```OOPGP.R```. The major method in the ```Simulate``` class is the ```simulate``` method. All the other methods and functions in other files are for supporting the ```simulate``` method of the ```Simulate``` class.

```
├── generate_setting
│   └── expert_sampling.R
├── run_one_setting.sh
├── setpath.R
└── workhorse
    ├── add_noise.R
    ├── main.R
    ├── max_dist.R
    ├── OOPGP.R
    ├── prepare_data.R
    ├── screen_index_helper.R
    └── update_train_pool.R

```


### Acknowledgement
This work was supported by an NSF award.
