# Final Course Project 2021
## Averaging Weights Leads to Wider Optima and Better Generalization

The code in this repository implements three loss optimization algorithms: conventional SGD, SWA and improved SWA. 
For each algorithm, we used the VGG16 model and evaluated the model on eleven different dataset taken from https://pytorch.org/vision/stable/datasets.html/ 

### About the code
The code is based on the paper authors' code which is available in https://github.com/timgaripov/swa.
We extended their code and implemented our project in Google Collaboratory in order to get GPU and memory resources. 
(However, one can download the code as a regular python file and run the code with the corresponding arguments as shown in the author's repository)

To run the code using the Collab notebook we refer to the function 'get_args' and to the makred arguments:
![alt text](https://github.com/LiadNahum1/FinalProject/blob/master/%E2%80%8F%E2%80%8Fargs.PNG)

Parameters:
* ```DATASET``` &mdash; dataset name
* ```EPOCHS``` &mdash; number of training epochs
* ```LR_INIT``` &mdash; initial learning rate
* ```SWA``` &mdash; activate SWA algorithm
* ```SWA_START``` &mdash; the number of epoch after which SWA will start to average models
* ```SWA_LR``` &mdash; SWA learning rate 
* ```IMPROVED``` &mdash; activate inproved algorithm

### Usage
In order to run the Collab notebook, change the default values of the marked parameters according to the current execution. <br />
**To Run Conventional SGD**:
* change ```DATASET``` default to be the wanted dataset name 
* ```EPOCHS``` and ```LR_INIT``` defaults are not important because they are the hyper-parameters and on SGD we apply hyper-parameters optimization
* change  ```SWA``` default to be False
* change  ```IMPROVED``` default to be False

**To Run SWA**:
* change ```DATASET``` default to be the wanted dataset name 
* denote the number of epochs determined by the optimization for SGD for the same dataset as B. change ```EPOCHS``` default to be 1.5*B
* denote the lr_init determined by the optimization for SGD for the same dataset. change ```LR_INIT``` default to be the same value. 
* change  ```SWA``` default to be True
* change ```SWA_START``` default to be 0.75*B. 
* change ```SWA_LR``` default to be the same as ```LR_INIT``` 
* change  ```IMPROVED``` default to be False <br />
(We implemented the constant learning rate schedule version)

**To Run Improved Algorithm**:
* change ```DATASET``` default to be the wanted dataset name 
* denote the number of epochs determined by the optimization for SGD for the same dataset as B. change ```EPOCHS``` default to be the same value.
* denote the lr_init determined by the optimization for SGD for the same dataset. change ```LR_INIT``` default to be the same value. 
* change  ```SWA``` default to be True
* change ```SWA_START``` default to be 0.5*B. 
* change ```SWA_LR``` default to be ```LR_INIT``` + 0.02 
* change  ```IMPROVED``` default to be False

### Results
The results can be seen in the file "results.xlsx". 
For each dataset (appears in different color in the file), we calculated the requested metrics using the 3 algorithms.
The reffered metrics are: Accuracy, TPR, FPR, Precision, AUC, PR-Curve, Training time, Inference time for 1000 instances.

For example, results for dataset 'SVHN':

![alt text](https://github.com/LiadNahum1/FinalProject/blob/master/result_example.PNG)

### Reproducing the Results
To reproduce the results, just insert the arguments corresponding to each dataset and each algorithm as explained above while ```LR_INIT``` and ```EPOCHS``` are the values written in the hyper-parameters column in the 'results.xlsx' report. 
