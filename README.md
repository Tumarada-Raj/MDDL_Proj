Name: Raj Mohan Tumarada
Matriculation Number: 7015640
Purpose: Final project submission as part of Model Driven Deep Learning Lab for Image Analysis (MDDL) course.



PyTorch implementation of MoDL: Model Based Deep Learning Architecture for Inverse Problems 

Official code: https://github.com/hkaggarwal/modl



## Reference paper

MoDL: Model Based Deep Learning Architecture for Inverse Problems  by H.K. Aggarwal, M.P Mani, and Mathews Jacob in IEEE Transactions on Medical Imaging,  2018 

Link: https://arxiv.org/abs/1712.02862

IEEE Xplore: https://ieeexplore.ieee.org/document/8434321/


## Project Goals
1)Understanding and describing the methodology in the paper, and where it differs and improves upon previous works
2)Clean reimplementation following modern coding practices in either TF or pytorch
3)Comparison to using a pretrained denoiser instead of end-to-end training

## Comments 
-Fulfilled all the project goals
-The training details along with tensorboard logs were present in  MDDL_proj.ipnyb file 
-For tensorboard the following runs are the final(base_modlt,k=10/train, base_modlptw,k=10/train, base_modlns,k=10/train, base_modlt,k=10/test, base_modlptw,k=10/test, base_modlns,k=10/test)
-Attaching the report which briefs about paper and its results
-Not submitting the dataset as it is roughly around 3 GB if necessary can be downloaded from the below link


## Dataset

The multi-coil brain dataset used in the original paper is publically available. You can download the dataset from the following link and place it under the `data` directory.

**Download Link** : https://drive.google.com/file/d/1qp-l9kJbRfQU1W5wCjOQZi7I3T6jwA37/view?usp=sharing


## Configuration file

The configuration files are present `config` folder. All the parameters are set same as the paper.

Configuration files for K=1 and K=10 are provided. We first train K=1 model and then train the K=10 models using the weights of K=1 model fot End-to-End training.
modl,K=1.yaml -----------> trains K=1 model first.
modlt,K=10.yaml ---------> trains the full model as per the configuration CG-ET-WS.
modlptw,K=10.yaml -------> trains the full model as per the configuration CG-PD-NS.
modlns,K=10.yaml --------> trains the full model as per the configuration CG-ET-NS.



## Train

You can change the configuration file for training by modifying the `train.sh` file with suitable .yaml file.

```
scripts/train.sh
```

## Test

You can change the configuration file for testing by modifying the `test.sh` file with suitable .yaml file.

```
scripts/test.sh
```

## Saved models

Saved models are provided.
K=1:  `workspace/base_modl,k=1/checkpoints/final.epoch0049-score37.3294.pth`
K=10: `workspace/base_modlt,k=10/checkpoints/final.epoch0049-score39.6521.pth`
K=10: `workspace/base_modlptw,k=10/checkpoints/final.epoch0049-score33.4335.pth`  ----> Model with pretrained weights
K=10: `workspace/base_modlns,k=10/checkpoints/final.epoch0049-score34.5012.pth`   ----> Model without weight sharing
