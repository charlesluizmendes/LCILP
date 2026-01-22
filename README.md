# Environment 

## Configuration

First of all, we need to create a Python environment with Anaconda:

```
conda create -n lcilp python=3.8 -y
conda activate lcilp
```

## Packages

Install for all dependency:

```
$ pip install -r requirements.txt
```

Or, if you prefer, install the dependencies one by one:

```
pip install torch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0 --index-url https://download.pytorch.org/whl/cu121
pip install dgl==2.4.0+cu121 -f https://data.dgl.ai/wheels/torch-2.4/cu121/repo.html
pip install lmdb
pip install matplotlib
pip install scikit-learn
```

# Execution

## Dataset

First, we'll clone the original Grails dataset and copy it to the data repository:

```
git clone https://github.com/kkteru/grail.git
cp -r grail/data/* LCILP/data/
```
```
rm -rf data/WN18RR_v1/subgraphs_en_True_neg_1_hop_3
```

## Train

Now we will begin training the model:

```
python train.py -d WN18RR_v1 -e test
```

## Test

Finally, let's run the model tests:

```
python test_ranking.py -d WN18RR_v1_ind -e test
python test_auc.py -d WN18RR_v1_ind -e test
```