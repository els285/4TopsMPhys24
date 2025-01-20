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
    **We should work on the `main` HyPER git branch** which is the one you are on by default when you git clone HyPER
  
  2. HyPER takes `.h5` files as inputs. Ethan will provide the input `h5` files.




# Technical
## Writing awkward arrays to h5
ROOT files and awkward arrays are as you know "ragged" i.e. arrays are not all the same length, but vary depending on things like number of jets in an event.
For making oru machine learning scripts more modular and using HyPER, we should write our outputs to `h5`, which is the preferred way to save non-ragged numpy arrays.
This means we have to "pad" our awkward arrays, convert them to numpy and save them using `h5py`.

I was going to write more detailed instructions but I cba so I just point you to my parser as an example: [https://github.com/els285/PhenoSimp/blob/dev/tools/write_to_hyper_input.py](https://github.com/els285/PhenoSimp/blob/dev/tools/write_to_hyper_input.py)

