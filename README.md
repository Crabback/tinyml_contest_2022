# Python example code for the ACM/IEEE TinyML Contest at ICCAD 2022

# Code Implementation:
- All code about data preprocessing in data_preprocessing.py
- Helper functions, like plot accuracy and loss, read dateset, in __help_code_demo.py__
- Differences between training py and testing py
  - Training and testing with validation in __training_save_deep_models_valid_split.py__ and __testing_performances_valid_split.py__
  - Original model (without validation) in __training_save_deep_models.py__ and __testing_performances.py__
  - Training and testing with Fourier Transform in __training_save_deep_models_fft.py__ and __testing_performances_fft.py__
  - Other training and testing file can be saved as training_model_[xxx].py and testing_[xxx].py
- Logistic Regression model in log_reg.py
- Data_indices stores indices with corresponding file name in './data_indices/'
- __Model evaluation records__ in './records/' with name structure seg_stat_[xxx].py
- All models codes placed in './models/'
  - model_1.py is the original model
  - Other model can be named as [Model_architecture].py
- Saved model in './saved_models'

## What's in this repository?

This repository contains a simple example to illustrate how to train the model with pytorch and evaluate the comprehensive performances in terms of detection performance, flash occupation and latency. You can try it by running the following commands on the given training dataset. 

For this example, we implemented a convolutional neural network (CNN). You can use a different classifier and software for your implementation. 

This code uses four main scripts, described below, to train and test your model for the given dataset.

## How do I run these scripts?

You can run this classifier code by installing the requirements

    pip install requirements.txt

and running

    python training_save_deep_models.py 
    python testing_performances.py

where `models` is a folder of model structure file, `saved_models` is a folder for saving your models, `data_indices` is a folder of data indices (the given training dataset has been partitioned into training and testing dataset, you can create more partitions of the training data locally for debugging and cross-validation), and `records` is a folder for saving the statistics outputs. The [TinyML Contest 2022 web-page](https://tinymlcontest.github.io/TinyML-Design-Contest/Problems.html) provides a description of the data files.

After running the scripts, one of the scoring metrics (i.e., **F-B**) will be reported in the file *seg_stat.txt* in the folder `records`. 

## How do I deploy the model on the board?

In this example, we will deploy the model on the board NUCLEO-L432KC with STM32CubeMX and the package X-Cube-AI. 

You can firstly convert the model to onnx format by running

    python pkl2onnx.py 

Once we obtain the onnx model file, we could deploy the model on the board by following the instructions described in [README-Cube.md](https://github.com/tinymlcontest/tinyml_contest2022_demo_example/blob/master/README-Cube.md). The other two metrics, **Flash occupation** and **Latency** could be obtained based on the reports from STM32CubeMX. 


## How do I obtain the scoring?
After training your model and obtaining test outputs with above commands, you could evaluate the scores of your models using the scoring function specified in [TinyML Contest 2022 evaluation](https://tinymlcontest.github.io/TinyML-Design-Contest/Problems.html). 

