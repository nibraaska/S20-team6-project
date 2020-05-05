# Team LSTM
### Members
1. George Boktor 
2. Nibraas Khan
3. Ruj Haan
4. Michael McComas
5. Ramin Daneshi

## Demo (With Python 3)
For as long as humans have participated in the act of communication, concealing information in those communicative mediums or concealing any traces of communication has manifested into an art of its own. An important technique used to conceal any traces of communication called steganography has been used in many domains including government level communication and encoding harmful media in innocuous media such as in phishing emails. Our work aims to crack a popular steganography algorithm and running our code will highlight exactly how to do that. 

We will have one demo file, ```cycle_gan.ipynb``` to demonstrate quick and simple examples of our results. The notebook will highlight the capabilities of our Cycle Generative Adversarial Networks (CycleGANs) algorithm to crack the Least Significant Bit (LSB) Steganography technique.

Our demo uses Jupyter Notebook, so the most basic steps needed to run our code is:

1. Install Jupyter Notebook (https://jupyter.org/install)
2. Open ```cycle_gan.ipynb```

Below are more detailed instructions on how to work with our code including working with our packages, working with our datasets, manipulate our network, tuning hyper-parameters, and saving results. There is much more to be explored once you understand how to base CycleGAN algorithm works!

### Quick Start Guide
The following scripts and ipynb notebook executed in this order will allow you to install all the packages, install all the datasets, pre-process the data, and run the code (assuming you have Jupyter Notebook installed):

1. ```demo/setup```
2. ```demo/get_data.py```
3. ```demo/preprocess.py 15 10```
4. ```demo/cycle_gan.ipynb```

These steps will set up everything needed to run the code in ```cycle_gan.ipynb```.

### Detailed Steps

<details>
<summary>Installing Anaconda and Dependencies</summary>
<br>

#### Installing Anaconda and Dependences
    
</details>
    
<details>
<summary>Getting Datasets and Pre-processing</summary>
<br>

#### Getting Datasets and Pre-processing
    
    To grab data for this project, perform the following command using the get_data.sh file:
    
    ```./get_data```
    
    This bash executable will gather data from a URL and unzip the files. It will create four directories titled set1, set2, decodedArray, and encodedArray. In these directories it will dynamically name each file based on the count and then continue to the next directoy. To gather different data, simply change the URL located at the top line of the get_data.sh file to the desired destination.
    
    Our preprocess.py file will take a file from set1 and set2 and then encode it. It will be named dynamically and stored in our encodedArray directory created earlier in get_data.sh. The program will then take the encodedArray file, create a decoded version, and place it inside the decodedArray directory.

</details>
<details>
<summary>Training, Testing, Saving, and Manipulating the Model</summary>
<br>

#### Training and Saving

The code for training the CycleGAN model is found in ```demo/train.py```. The hyper-parameters, dataset, and saving mechanisms can be tweaked inside this file. 
    
To exceuate training run: 

```python3 demo/train.py [bit size]```
    
This command will run the code using the data from ```demo/get_data.py```, first 10 images from set 1 and first 5 images from set 2 as training data from the specified bit size (0-8), and will save the results in results in ```demo/checkpoints/cycle_gan_train_[bit size]```. All of these can be changed in the ```demo/train.py``` file.
    
#### Testing
    
After training is done, you can run: 
    
```python3 demo/test.py [bit size]```
    
The ```demo/test.py``` file assumes that you have trained in the bit size you are testing and the checkpoints have been saved in ```demo/checkpoints/cycle_gan_train_[bit size]```. The test file will generate an image, ```test.png``` that shows the results of the algorithm. The location of the checkpoints and the name of the file can be modified in ```demo/test.py```.
    
</details>
    
<details>
<summary>Tuning Hyper-parameters</summary>
<br>

#### Tuning Hyper-parameters 

To tune our hyper-parameters we used Bayesian Optimization. It tunes the hyper-parameters to get the best results for model performance.

The code for training the model using bayesian optimization can be found in ```demo/cycle_gan_bayes.py```. 
  
To execute Bayesian Optimization run: 

```python3 demo/cycle_gan_bayes.py [bit size] ```

The command will run the cycle gan model using bayesian optimization, for each iteration it will store the hyperparameters and the performance in ```demo/logs[bit size].json``` file. The search space of Bayesian Optimization can be changed in the file. 
    
</details>
