# Take an Emotion Walk

This is the official implementation of the paper Take an Emotion Walk: Perceiving Emotions from Gaits Using Hierarchical Attention Pooling and Affective Mapping. Please add the following citation in your work if you use our code:

```
@InProceedings{bhattacharya2020taew,
author="Bhattacharya, Uttaran
and Roncal, Christian
and Mittal, Trisha
and Chandra, Rohan
and Kapsaskis, Kyra
and Gray, Kurt
and Bera, Aniket
and Manocha, Dinesh",
editor="Vedaldi, Andrea
and Bischof, Horst
and Brox, Thomas
and Frahm, Jan-Michael",
title="Take an Emotion Walk: Perceiving Emotions from Gaits Using Hierarchical Attention Pooling and Affective Mapping",
booktitle="Computer Vision -- ECCV 2020",
year="2020",
publisher="Springer International Publishing",
address="Cham",
pages="145--163",
isbn="978-3-030-58607-2"
}
```

## Installation Requirements

Our scripts have been tested on Ubuntu 18.04 LTS with
- Python 3.6
- Cuda 10.2
- cudNN 7.6.5

We recommend using an Anaconda virtual environment. If Anaconda is not already installed, [Install Anaconda](https://www.anaconda.com/distribution/#download-section) and run
``` 
conda env create -n taew -f environment.yml
```
from within the project directory

## Download datasets and network weights

Run the following command from within the project directory to download and extract the sample datasets and network weights:
``` 
sh download_data_weights.sh
```

We have used the Emotion-Gait dataset for this work. The full dataset is available for download here: [https://go.umd.edu/emotion-gait](https://go.umd.edu/emotion-gait).

## Evaluation

1. Activate the conda environment
```
conda activate taew
```
2. Run the evaluation script
For dgnn evaluation:
```
python evaluate.py --dgnn 
```
For stgcn evaluation:
```
python evaluate.py --stgcn
```
For lstm network evaluation:
```
python evaluate.py --lstm
```
For step evaluation:
```
python evaluate.py --step
```
For taew evaluation:
```
python evaluate.py --taew
```

## Details for using taew_net as stand-alone
1. ```main.py```is the starting point of the code. It is runnable out-of-the-box once the datasets directory is downloaded and extracted. It also contains the full list of arguments for using the code.
2. ```utils/loader.py``` is used for loading the data and the labels. Labels are only available for the annotated part of the data.
3. ```utils/processor.py```contains the main training routine with forward and backward passes on the network, and parameter updates per iteration.
4. ```net/hapy.py``` contains the overall network and description of the forward pass.
