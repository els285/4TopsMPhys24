# Semester 2 Start

## DNN Work 
* Make DNN into a Python script which can be run in the terminal as:
```bash
python run_DNN.py --train_file=train_file.h5 --test_file=tset_file.h5
```
This involves writing the inputs to `h5` which is good practice for HyPER. See section below on h5. 
* Plot the loss curves for training.

  ## Running HyPER
  We will focus on the 0L channel to start.
  1. Install HyPER: Use [Simon's tutorial on running HyPER on Chicago](https://github.com/els285/4TopsMPhys24/blob/main/Tasks/Semester2/HyPERonChicago.md) to get set up:

     Conda is a package manager which allows us to install all the necessary PyTorch-associated tools for grpah neural networks. Simon's instructions describe how to:
      * Install `conda` (via miniforge)
      * Build the conda environment
    
    ** We should work on the `main` HyPER git branch** which is the one you are on by default when you git clone HyPER
  
  2. HyPER takes `.h5` files as inputs. Ethan will provide the input `h5` files.
