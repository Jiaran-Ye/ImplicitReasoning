# Multi-Hop Implicit Reasoning in Transformers

## Overview

This repository contains the code for reproducing the experiments in our paper **"How Does Transformer Learn Implicit Reasoning?"** . In this work, we explore how implicit multi-hop reasoning emerges during training in transformers. We also propose several novel techniques, such as *cross-query semantic patching* and a *cosine-based representational lens*, to analyze the behavior and internal representations of transformers during multi-hop reasoning.

## Structure of the Repository

- **notebooks/**: This folder contains all the Jupyter notebooks that are essential for replicating and understanding our experiments. The notebooks include the data preparation, new methods, and analysis steps.
  - **cosine_metrics.ipynb**: Computes the cosine-based representational lens to analyze model behavior.
  - **data_preparation.ipynb**: Code for constructing the datasets and preparing the data for training.
  - **training_dynamics.ipynb**: Drawing the model's learning dynamics during training.
  - **cross_query_semantic_patching.ipynb**: Implements the cross-query semantic patching technique to locate postion that encode Immediate entities.
  - **logit_lens.ipynb**: Code for probing the intermediate states using the logit lens.

- **README.md**: This file, which explains how to replicate the experiments and the structure of the repository.

## Setup Instructions

To replicate the experiments, follow these steps:

### 1. Clone the previous work's repository

Our work builds upon [GrokkedTransformer](https://github.com/OSU-NLP-Group/GrokkedTransformer). Please clone their repository and follow their instructions for setting up the environment and training the model.

```bash
git clone https://github.com/OSU-NLP-Group/GrokkedTransformer.git
cd GrokkedTransformer
# Follow the setup instructions in their README
``` 

### 2. Data Preparation

In the `notebooks/data_preparation.ipynb`, you will find the code to prepare the dataset used in our experiments. Run this notebook to generate the data necessary for the training process.

### 3. Training and Experiment Reproduction

After setting up the environment and preparing the data, use the training code provided by the previous work (GrokkedTransformer). The training code will be similar to what is explained in their README.

> ⚠️ **Important Note on Data Path**  
> The original GrokkedTransformer training scripts expect the dataset to be located in a `data/` folder relative to their repository root, i.e., `data/<your_dataset>/`.  
>  
> However, our `data_preparation.ipynb` script generates data in a `data/` folder located at the root of our project (at the same level as the `notebooks/` directory).  
>  
> **To avoid errors when training, you have two options:**
> 
> 1. **Modify the training script:**  
> In the GrokkedTransformer training script (e.g., `train.sh`), update the following line:
> 
> ```bash
> DATASET=data/$1/
> ```
> to:
> ```bash
> DATASET=../data/$1/  # or the actual relative path to your generated data
> ```
>
> 2. **Copy the generated data:**  
> Alternatively, you can copy the generated data into their expected directory:
> 
> ```bash
> cp -r data/ <path_to_GrokkedTransformer_repo>/data/
> ```

Once the model is trained, you can use our methods in the `notebooks/` folder to analyze the trained model and replicate the results of our experiments.

### 4. Experiment Analysis

To analyze the results, use the following notebooks:
- **training_dynamics.ipynb**: This notebook draws the model's learning dynamics during training.
- **logit_lens.ipynb**: This notebook tries to understand the learning dynamics using a popular tool calls logit lens.
- **cosine_metrics.ipynb**: This notebook computes the cosine metrics for understanding the representational space of the model.
- **cross_query_semantic_patching.ipynb**: This notebook helps you locate the postion that encode Immediate entities using our cross-query semantic patching technique.

## Contact Information

For any questions or issues, please feel free to contact the authors.
