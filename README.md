# E2E-TBSA
Source code of our AAAI paper on End-to-End Target/Aspect-Based Sentiment Analysis, forked
from [lixin4ever](https://github.com/lixin4ever/E2E-TBSA). In this fork a `DockerFile` is 
added that can be used to run the code in this repository out of the box. 

# Using the docker image

The DockerFile automates all steps in the below Manual Installation section. This includes
installing dependencies, and installing the default embedding. Some steps do not match
the description below. For instance, `DyNet 2.0.2` is not installed, instead, `DyNet` is 
installed from GitHub and compiled using `cython`, `build-essential` and `cmake`.

Please note that building for the first time takes a while, and results in a large image.
The first step of the docker build is downloading and unpacking the embedding. The
download itself is 2 GB, and the unpackked embedding has a size of ~5GB. 

Build using:

```
docker build -t 2e2-absa
```

Run using: 
```
docker run --rm -it 2e2-absa <ARGS>
```

For `<ARGS>` see `main.py`.

## Issues

Note that only the default embedding is supported, using other embeddings wil result in
an error. In case you want to use additional embeddings, please extend the DockerFile. 

# Manual installation

## Requirements
* Python 3.6
* [DyNet 2.0.2](https://github.com/clab/dynet) (For building DyNet and enabling the python bindings, please follow the instructions in this [link](http://dynet.readthedocs.io/en/latest/python.html#manual-installation))
* nltk 3.2.2
* numpy 1.13.3

## Data
* **rest_total** consist of the reviews from the SemEval-2014, SemEval-2015, SemEval-2016 restaurant datasets.
* **laptop14** is identical to the SemEval-2014 laptop dataset.
* **twitter** is built by [Mitchell et al.](https://www.aclweb.org/anthology/D13-1171) (EMNLP 2013). 
* We also provide the data in the format of conll03 NER dataset.

## Parameter Settings
* To reproduce the results, please refer to the settings in **config.py**.

## Environment
* OS: REHL Server 6.4 (Santiago)
* CPU: Intel Xeon CPU E5-2620 (Yes, we do not use GPU to gurantee the deterministic outputs)

# Citation
If the code is used in your research, please star this repo and cite the original paper as follows:
```
@inproceedings{li2019unified,
  title={A unified model for opinion target extraction and target sentiment prediction},
  author={Li, Xin and Bing, Lidong and Li, Piji and Lam, Wai},
  booktitle={Proceedings of the AAAI Conference on Artificial Intelligence},
  pages={6714--6721},
  year={2019}
}
```


