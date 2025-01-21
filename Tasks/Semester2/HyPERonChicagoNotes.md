# Using HyPER on Chicago

## Install a Conda package manager

If you have never used ```conda``` on Chicago before, you need to install a ```conda``` package manager.  
A simple way to do it is to go on the [miniforge Github repository](https://github.com/conda-forge/miniforge) and to follow the instructions under _Install_ for **_Unix-like platforms (macOS & Linux)_**.

## HyPER installation + environment setup

Copy the HyPER web url on the [Github repository](https://github.com/tzuhanchang/HyPER) (click on the green **Code** button).  

On Chicago, go to the directory you want to work in and clone the HyPER repository there:

```
git clone HyPER_URL
```

Once this is done, you can go inside the "_HyPER_" directory and create the ```conda``` environment HyPER needs to run (it will be named "_HyPER_"):

```
conda env create -f environment_linux.yaml
```

If everything worked, you should be able to work in the environment after entering:
```
conda activate HyPER
```

## Create and use a Jupyter notebook on Chicago

Every task HyPER can accomplish has its length greatly reduced when using a GPU (_i.e._ not only relying on CPUs).  
A simple way to use a GPU on Chicago is to work from a Jupyter notebook.  

For that, go on the [Analysis Facility at UCHICAGO](https://af.uchicago.edu/) website.  
From there, click on:  
 * Services
 * JupyterLab
 * Configure notebook

You should then be able to chose the configuration of your notebook, which parameters (aside from the notebook name) are the following:
* **CPU cores** : the more the better, can ask up to 16.
* **Memory** : again more is better, can ask up to 32.
* **GPU instances** : I usually ask for one big GPU, but it might be possible to run HyPER on 4 smaller GPUs. 
* **GPU model** : here from my experience the best is to get the _NVIDIA A100 (Whole)_ but when its not available the _NVIDIA Tesla V100_ is half as fast, which is still reasonable. You can check which GPUs are available by **clicking on the blue info icon** next to _GPU model_.
* **Duration** : Can ask up to 72 hours.
* **Image** : Select **ml-platform:conda**, else you will not be able to use HyPER.

Once you are satisfied with the parameters, click on _Create notebook_. The status of the notebook should change to _Ready_ in a few seconds/minutes.

Once the notebook is ready, click on its name. It will open a window on which you can open a terminal by clicking the "_Terminal_" button.  
To use HyPER from this terminal, you need to activate the "_HyPER_" environment:
```
conda activate HyPER
```

After that, just go to your "_HyPER_" directory and you will be able to use HyPER!

## Using HyPER

Before you want to run HyPER for any task, check that you are satisfied with the parameters in the configuration file you want to use (located in the "_configs_" directory).

### Training HyPER

To train a new HyPER model, use the following command with the config file of your choice:
```
python -m HyPER.train --config-name=myConfigName
```

By default it will create a "_HyPER_logs_" directory which contains the outputs of the training. 


To visualise the results of the training in real time, it is recommended to use the **Tensorboard** extension on VS Code.  
After installing the extension, launch it by typing "_>Python: Launch Tensorboard_" in the VS Code search bar.  
After a few seconds, you will be offered 3 choices: click on "_Select another folder_", then find the directory containing the training outputs ("_HyPER_logs_" by default) and press "_Ok_".

You now have access to the details of the training of all models stored in the directory. To investigate a specific model, check its corresponding box on the left.  
On the middle of the window there are graphs, the most interesting ones are under "_fuzzy_accuracy_" and "_loss_", where you can see the evolution as a function of training steps of respectively the validation edge and hyperedge accuracy and both the training and validation loss functions.

### Predicting with HyPER

To reconstruct the events of a certain dataset with a certain HyPER model, use the following command with the config file of your choice:
```
python -m HyPER.predict --config-name=myConfigName
```

### Converting HyPER model to onnx format

To convert a certain HyPER model to the onnx format, use the following command with the config file of your choice:
```
python -m HyPER.onnx --config-name=myConfigName
```