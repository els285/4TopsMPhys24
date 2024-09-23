# 3tops vs 4tops

This introductory task is designed to get you acquainted with using Python tools for analysing high-energy physics datasets.
You will first examine the `4tops` dataset: loading and manipulating the data, applying various filters to the data (in experimental physics we call this "applying selection cuts"), and then plotting histograms of various kinematic quantities.
You will then use the analysis tools you have developed to compare the `4tops` dataset to the `3tops dataset`.

Inital 4tops dataset found in Google Drive: `/Partonic/4tops_partonic_skimmed_2409.root`.

## The Datasets
Particle physics datasets from collider experiments contain many separate **events**, each of which represents a separate proton-proton collision. 
Each event is characterised by some meta-data plus the kinematics of the various particle which participate in the event.
We will actually consider simulated data where a specific set of particles (four top quarks) is produced at a collision energy of 13 TeV.
Data will be in the form of ROOT files (unless I get lazy).

## Tutorial 
Andy Pilkington has a very basic example on how to use the `Scikit-HEP` software stack to analyse ROOT files. 
[This example is linked here](https://github.com/heppilko/ParticlePhysics-simulation-and-analysis/blob/main/Examples/analysis_python.ipynb).
You will build on this basis example.
Docuemntation for all the relevant Python modules [here](https://scikit-hep.org/).
Python modules used:
* `uproot`: for reading and writing ROOT files.
* `awkward`: the backend for the type of array of events we will analyse.
* `vector`: package for building 4-momenta vectors.
* `matplotlib`: biggest Python plotting package, which has basic histogramming functionality.


Additional useful modules:
* `numpy`: super powerful (non-ragged) array manipulation.
* `boost-histogram`: more powerful histogramming tool which I recommend you use.
* `mplhep`: package built on `matplotlib` specifically for making HEP plots.

## Tasks A: Basic Analysis
Put all saved histograms in a set of slides. I think it's a really good idea to keep track of your research as you go using Google Slides (or equivalent) where you can write out what you've done and include the plots. 

#### Loading, Filtering and Plotting
* Load the 4tops data
* Apply a filter to select only events where `top_pt > 200`
* Make histograms of the branches `top_e` , `anti_top_eta`
* Save these histograms as PNGs/PDFs/whatever

#### Using vector (look at the vector documentation)
* Load the 4tops data
* Apply the selections: top_pt > 50 and -2.4 < top_eta < 2.4 , and similarly for anti_top (remember this selection is applied per-event, so an event might meet one condition and not the other, but it has to meet both to pass the selection).
* Build a `vector` array of top quarks, and a similar array of antitop quarks.
* Build the combined 4tops system by adding your vector arrays e.g. `top1 + top2 + antitop1 + antitop2`
* Apply a selection to the 4tops system to retain only events where the invariant mass > 500
* Plot and save histograms of: 4tops invariant mass, deltaR between the two quarks which have the highest pt.

## Tasks B: Comparign 3tops to 4tops
Ethan to do sort out 3tops file first.




