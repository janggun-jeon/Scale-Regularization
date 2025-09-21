# RioGNN-sr
 Effects of Scale Regularization in Fraud Detection Graphs

![Image](https://github.com/user-attachments/assets/68c8eb96-e605-4d74-a1f4-00c91544fca6)

[https://doi.org/10.3390/electronics14183660](https://doi.org/10.3390/electronics14183660)

Electronics 2025, 14(18), 3660 <br>
ISSN:2079-9292      
eISSN:2079-9292

## Repo Structure

The repository is organized as follows:
- `data/`: dataset folder
    - `Amazon.zip`: Data of the dataset Amazon;
- `log/`: log folder
- `model/`: model folder
    - `graphsage.py`: model code for vanilla [GraphSAGE](https://github.com/williamleif/graphsage-simple/) model;
    - `layers.py`: RioGNN-sr layers implementations;
    - `model.py`: RioGNN-sr model implementations;
- `RL/`: RL folder
    - `actor_critic.py`: RL algorithm, [Actor-Critic](https://github.com/llSourcell/actor_critic);
    - `rl_model.py`: RioGNN-sr RL Forest implementations;
- `utils/`: functions folder
    - `data_process.py`: transfer sparse matrix to adjacency lists;
    - `utils.py`: utility functions for data i/o and model evaluation;
- `train.py`: training and testing all models


## Example Dataset

We build different multi-relational graphs for experiments in two task scenarios and three datasets: 

| Dataset  | Task  | Nodes  | Relation  |
|-------|--------|--------|--------|
| Amazon  | Fraud Detection | 11,944  | upu, usu, uvu, homo |

## Run on your Datasets

To run RioGNN-sr on your datasets, you need to prepare the following data:

- Multiple-single relation graphs with the same nodes where each graph is stored in `scipy.sparse` matrix format, you can use `sparse_to_adjlist()` in `utils.py` to transfer the sparse matrix into adjacency lists used by RioGNN-sr;
- A numpy array with node labels. Currently, RioGNN-sr only supports binary classification;
- A node feature matrix stored in `scipy.sparse` matrix format. 


## How to Run
You can download the project and and run the program as follows:

###### 1. Unzip `amazon.zip` in the dataset folder `\data`;
```bash
unzip data/amazon.zip
```
\* Note that all datasets need to be unzipped in the folder `\data` first;
###### 2. Install the required packages using the `requirements.txt`;
```bash
pip3 install -r requirements.txt
```
###### 3. Run `data_process.py` to generate adjacency lists of different dataset used by RioGNN-sr;
```bash
python data_process.py
```
###### 4. Run `train.py` to run RioGNN-sr with default settings.
```bash
python train.py --embed_rescalied
```
###### 4.1. Run `mecro.sh` to run RioGNN-sr with default iteratively.
```bash
# '72' is the seed value
mkdir log/amazon/seed-72
mkdir log/amazon/seed-72/log
sh mecro.sh
```

\* To run the code, you need to have **Python 3.10**. 

## Citation
If you use our code, please cite the paper below:
```bibtex
@article{jeon2025effects,
  title={Effects of Scale Regularization in Fraud Detection Graphs},
  author={Jeon, Janggun and Ahn, Junho and Kim, Namgi},
  journal={Electronics},
  volume={14},
  number={18},
  pages={3660},
  year={2025},
  publisher={MDPI}
}
```
