# C-NN-CDH

## Introduction

The code contains everything you need to conduct the experiment, described in paper Case-based Classification using Neural Network Based Case Adaptation, to compare the accuracy and balanced accuracy of following systems:

1-NN, 3-NN, neural network, normal C-CDH, C-NN-CDH, EAC-NN-CDH, C2C-NN-CDH.

Section "Data Preparation" includes dependencies and code to build the neural networks.

Section "Separate the training and testing" contains the training and testing procedures.

Section "Graph and report" contains functions to do graph.

Section "KFOLD CODE" contains necessary code to run a k-fold experiment on a data set.

Section "Dataset loading: XXX" load a data set XXX and preprocess it.

Section "Trying 10 fold: Credit dataset" runs the experiment with some hyperparameter settings.

Other sections are not necessary to run an experiment but kept there for potential extension.

## How to run an experiment

Run all sections before and include "Graph and report". This should prepare the dependencies, systems, training, testing and reporting code.

Run the section "KFOLD CODE"

Run a section "Dataset: XXX", and then Run "Trying 10 fold: XXX"

Note that you need to download the data set first and set the file path correctly. All data sets can be accessed through UCI repository.

The code can be run on a google colab environment easily.

## How to choose parameters

train_models() depends on following customizable parameters:

* EAC_adapt:0, no EAC; 1 EAC; 2 C2C-EAC
* pair_selection: 1, neighbor; 4, random pairs; 5, C2C pairs
* C2C IS ONLY USABLE WHEN EAC_adapt contains 2 and pair_selection contains 5 

You can change these parameters in "Trying 10 fold: XXX".

In kFoldExperiment() you can alter the number of runs

Certain details are not exposed therefore not easily customizable. For example, in train_models(), you may change the code to assemble adaptation examples. This is the code segment under the comment "#Assemble pairs". However, we do not expose the configuration because this is a design question depending on the task domain. Fine tuning such setting is beyond the purpose of this proof-of-concept experiment.

## Randomness

Following randomness exist in the program and can be set with a seed.

* In train_models(), train and validation split
* In train_models(), random pairs
* In section "KFOLD CODE", kf = KFold(n_splits=10, shuffle=True)

## Updates

1/20/2021 "classification experiment Unsegmented" added. This file contains the variants for unsegmented training adaptation examples. They are for variant (1,2)

The old file "classification experiment.ipynb" is for variant (0) and (3-5), along with baseline systems including neural net, 3-NN, and 1-NN.