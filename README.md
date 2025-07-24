# Offline-LD
This repository contains the official implementation of the paper "Offline Reinforcement Learning for Learning to Dispatch for Job Shop Scheduling"

## Requirements
- Python 3.11
- Pytorch 2.1.2
- Gymnasium 0.28.1
- Minari 0.5.1

To install all the requirements, run the following command:
```
pip install -r requirements.txt
```

## Explanation of the code

The code exits out of two components the dataset generation, used for training, and the training and evaluation of the models themself.

### Dataset Generation
The dataset generation consists of three parts: creating instance, creating solutions, and finally creating datasets. In the near future, we will make this process more accessible.
#### Creating instances
To create JSSP instance, you need to call "[generate_data.py](generate_data.py)". This file generates a NPY file which contains randomly generated instances for JSSP, based on the specifications in the file itself.
#### Creating solutions
The solution are in-turn found through constraint programming via the file "[create_data_cp_sat.py](Job_Shop_Scheduling_Benchmark_Environments_and_Instances/create_data_cp_sat.py)" in the folder "Job_Shop_Scheduling_Benchmark_Environments_and_Instances". This file generates solutions for the instances in a folder, whereby each solution is saved as a JSON file. 

#### Creating datasets
The datasets are created through the file "[create_dataset_from_data.py](main_code/create_dataset_from_data.py)" in the folder "main_code". This file creates the datasets from the generated instances and saves them as Minari datasets, which can easily be loaded in during training.

### Training
Training is done by either running "train_cql_qrdqn.py" or "train_cql_sac.py". The arguments are explained in the code itself.

### Evaluation
This file is used to evaluate the trained models, by either calling "eval_cql_qrdqn_all.py" or "eval_cql_sac_all.py". The arguments are explained in the code itself.

## Other Information
To create more solution, you can use the files "create_data_cp_sat.py" or "create_data_cp_sat_single_instance.py". I will update this code in the future, such that it is more easier to use. You can also use other solvers/heuristics to create data, but they need to be saved as a JSON file like in results_cp_sat. If you get stuck, you can always contact me and I will try to help you out.

## Contact
If you have any questions or discover a bug, please contact me at via [email](mailto:j.v.remmerden@tue.nl).

## Reference
If you found this code useful, please cite our work as follows:
```
@article{van2025offline,
	author = {Remmerden, Jesse van and Bukhsh, Zaharah and Zhang, Yingqian},
	journal = {Machine Learning},
	number = {8},
	pages = {191},
	title = {Offline reinforcement learning for learning to dispatch for job shop scheduling},
	volume = {114},
	year = {2025}}
```