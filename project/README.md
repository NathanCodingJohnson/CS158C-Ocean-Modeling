# California Tsunami Risk

## Project Description

In this project, I will experiment with the simulation of tsunamis to observe their impact on California and the Bay Area in particular.

I aim to answer the following science question with this project:

*Is it reasonably possible for the Bay Area to be hit by a Tsunami?*

In order to answer this question I will construct a model of the ring of fire, where subduction zone plate boundaries surround the Pacific Ocean. I will run several tsunami simulations in different locations on subduction zones with tsunami size being determined by a realistic estimation of movement from an earthquake at that point. I anticipate that there will be a combination of the location of the earthquake and the size of the earthquake that will cause the resulting tsunami to hit the Bay Area at a moderate intensity. 

For the initial conditions, I will use the most recent available ECCO Version 5 Model in December 2017. I will also construct the boundary and external forcing conditions based on this same ECCO Version 5 data. In order to analyze and visualize the results, I will create a movie for each simulation, showing the location of the tsunami on an hourly/semi-hourly rate as it travels across the Pacific. I may also create a graph of the water height in the Bay area to get a more detailed picture of the impact of a tsunami in the area.

## Reproducing Model Results

The following steps outline how to construct the model files, configure and run the model, and assess the model results.

### Step 1: Create the Model Files
Several input files need to be created to run the model. Generate the following list of files using the notebooks indicated in paratheses:
- Model Grid (notebooks/Creating Model Grid.ipynb)
- Bathymetry (notebooks/Creating Model Bathymetry.ipynb)
- Initial Conditions (notebooks/Creating Initial Conditions.ipynb)
- External Forcing Conditions (notebooks/Creating External Forcing Conditions.ipynb)
- Boundary Conditions (notebooks/Creating Boundary Conditions.ipynb)
The model files should be placed into the  `input` directory.

### Step 2: Add files to the computing cluster
Once the input files have been created, the model files can be transferred to the computing cluster. Begin by cloning a copy of [MITgcm](https://github.com/MITgcm/MITgcm) into your scratch directory and make a folder for the configuration, .e.g.
```
mkdir MITgcm/configurations/pacific_tsunami
```
Then, use the `scp` command to send the `code`, `input`, and `namelist` directories to your configuration directory. 

### Step 3: Compile the model
Once all of the files are on the computing cluster, the model can be compiled. Make a `build` directory in the configuration directory and run the following lines:
```
../../../tools/genmake2 -of ../../../tools/build_options/darwin_amd64_gfortran -mods ../code -mpi
make depend
make
```

### Step 4.1: Run the model without tsunami
After the compilation is complete, run the model with the wind. Move to the run directory, link everything from `input` and `code`, and the submit the job script:
```
sbatch cs185c00.slm
```

### Step 4.2: Run the model with tsunami
Next, run the model without wind to complete the experiment. Again, link everything from `input` and `code` to a directory called `run_tsunami`. Then, edit the `data` file to point to the modified ETAN file Created in the last part of the Creating Initial Conditions.ipynb. Then, submit the job script again to rerun the model.

### Step 5: Analyze the Results
There are two notebooks provided for analysis:
1. Analyzing Model Results

   This notebook is provided to have a quick look at spatial and temporal variations in the temperature field in the model with wind. It also generates the visualization provided in the figures directory.
   
2. Answering the Science Question
   
  This notebooks provided some analysis plot to address the science question posed above.
