# README for CA1_Cutsuridis

This model, originally written in NEURON and hoc by Cutsuridis et al (2009), has been adapted by M. Bezaire to be a hybrid NEURON+Python model for use in a summer course on computational modeling. The original code is available on [ModelDB](https://senselab.med.yale.edu/ModelDB/showmodel.cshtml?model=123815#tabs-1).

## Installation and Requirements


## Running the Code
The code can be run either via Python (with NEURON as a module) or stand-alone NEURON. When running the code via Python, command line arguments can be passed in to control the behavior of the model and also to alter specific parameters of the model.

###### NEURON+Python

When using Python to run the code, up to five command line arguments can be specified:
* **simname:** a unique name for the simulation; results files will be prefixed with this name
* **batchflag:** 1 or 0; 1=run the simulation in batch mode; write results to file and don't open the NEURON GUI interface.
* **plotflag:** 1 or 0; 1=create and display plots of results
* **scaleDown:** 1 or 0; 1=scale the model down to 1% of its original size, just for testing and debugging purposes
* **scaleEScon:** 1 or 0; 1=scale connections down as well, to speed up simulation time for testing and debugging purposes

To run a model with the name "2ndrun" that only creates output files and no plots, enter:

```
python -i HAM_StoRec_ser_trblsht.py "2ndrun" 1 0
```

To run a model that creates output files and plots, enter:

```
python -i HAM_StoRec_ser_trblsht.py "2ndrun" 1 1
```

To run a model that brings up the NEURON RunControl GUI and lets you click the Init & Run button, enter:

```
python -i HAM_StoRec_ser_trblsht.py "2ndrun" 0 0
```


###### NEURON

To use stand-alone NEURON to run the code, in a terminal enter:

```
nrngui HAM_StoRec_ser.hoc
```


## Model Background

###### ENCODING AND RETRIEVAL IN A MODEL OF THE HIPPOCAMPAL CA1 MICROCIRCUIT

This NEURON code implements a small network model (100 pyramidal cells and 4 types of inhibitory interneuron) of storage and recall of patterns in the CA1 region of the mammalian hippocampus. Patterns of PC activity are stored either by a predefined weight matrix generated by Hebbian learning, or by STDP at CA3 Schaffer collateral AMPA synapses.

**Reference:**
Cutsuridis, V., Cobb, S. and Graham, B.P. Encoding and Retrieval in a model of the hippocampal CA1 microcircuit. Hippocampus, in press, DOI 10.1002/hipo.20661, 2009.

**Abstract:**
It has been proposed that the hippocampal theta rhythm (4-7 Hz) can contribute to memory formation by separating encoding (storage) and retrieval of memories into different functional half-cycles (Hasselmo et al., 2002). We investigate, via computer simulations, the biophysical mechanisms by which storage and recall of spatio-temporal input patterns are achieved by the CA1 microcircuitry. A model of the CA1 microcircuit is presented that uses biophysical representations of the major cell types, including pyramidal (P) cells and four types of inhibitory
interneurons: basket (B) cells, axo-axonic (AA) cells, bistratified (BS) cells and oriens lacunosum-molecurale (OLM) cells. Inputs to the network come from the entorhinal cortex (EC), the CA3 Schaffer collaterals and medial septum. The EC input provides the sensory information, whereas all other inputs provide context and timing information. Storage is accomplished via a local STDP mediated hetero-association of the EC input pattern and the incoming CA3 input pattern on the pyramidal cell target synapses. The model simulates the timing of firing of
different hippocampal cell types relative to the theta rhythm in anaesthetized animals and proposes experimentally confirmed functional roles for the different classes of inhibitory interneurons in the storage and recall cycles (Klausberger et al., 2003, 2004). Measures of recall performance of new and previously stored input patterns in the presence or absence of various inhibitory interneurons are employed to quantitatively test the performance of our model. Finally, the mean recall quality of the CA1 microcircuit is tested as the number of stored patterns is increased.

Main file: [HAM_StoRec_par.hoc (parallel version)](HAM_StoRec_par.hoc)
           [HAM_StoRec_ser.hoc (serial version - VERY SLOW!)](HAM_StoRec_ser.hoc)

These files are configured to produce the results presented in figures 9 and 10 of the paper, showing recall of a stored pattern when the entorhinal cortex input is disconnected from the CA1 pyramidal cells and so pattern recall is cued  exclusively by CA3 Schaffer collateral input. Example results are in the Results directory, in which there are also Matlab files for plotting them. EC input can be restored by setting ECWGT to its non-zero value. Other results were produced by setting particular connection weight variables to 0 to remove certain synaptic pathways.

* *Note: Bug report, V. Cutsuridis and B. Graham, 21 Apr 2015
We have been informed of a bug in the IA mod file, used for the OLM interneuron first introduced in ModelDB ac. 28316. Simulations (those for Figs.9 and 10) were thus rerun with the bug fixed. There are small quantitative differences from the published results, but the model still works as described. To reproduce the published results, comment out the "rates(v)" line in the DERIVATIVE block of IA.mod.* *





