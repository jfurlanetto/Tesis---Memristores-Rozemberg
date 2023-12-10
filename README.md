# Thesis- VEOV Model
This repository is part of a master thesis work focused on the study of artificial neural networks using the VEOV (Voltage Enhanced Oxygen Vacancies) Model.  
The intensive use of artificial neural networks is enabling an impressive development in many areas of science and technology, mainly because of its application in machine learning techniques and, more generally, in artificial intelligence. These networks are mathematical abstractions with a strong biological inspiration, implemented in codes executed on electronic devices used implemented in codes executed on common electronic devices (software). An alternative strategy, which has been under exploration for a few years, is that the network can be coded in the same device (hardware), which would result in both the optimization of power consumption and the possibility of allowing alternative forms of calculation and information processing. of information. This approach itself includes a distinctive feature of biological neural tissues: the formation of intricate networks of components, simple and imperfect, with a very high degree of interconnection. An example of such systems are networks of metallic nanowires. They are usually self-assemblies of silver nanowires, a few tens of microns in size.
The intersections of these nanowires, mediated by the oxide coating or the polymer used in their fabrication, would be the equivalent of synapses in the aforementioned neuronal tissues. In this work we explore numerically-computationally the electrical transport properties of a nanowire network, comparing them with real experimental systems. Several models of the contact between nanowires (interfaces), particularly those with memristive properties, are analyzed in detail. The effect of environmental conditions, such as humidity and temperature, on their performance is also studied and the impact of connectivity on their electrical properties is evaluated. The results indicate that beyond the individual properties of the interfaces, the degree of connectivity and the topology of the network condition the electrical response obtained and allow us to outline recommendations for the design of a protocol for the electrical characterization of the associated experimental systems.
All files in the repository are in .ipynb format.  
All files must be downloaded and placed in the same directory.  
For more operational details on running the program see file "Instructions.pdf".

## Programs:
### Rozenberg Model 5.6i Pyspice.ipynb.
Main program: Defines the memristor parameters, creates the spatial arrays and the applied electrical signal and solves the network during the experiment cycle by calling the Memristorfunction and PySpicefunction functions. Exports the results of the experiment in a folder inside the directory (graphs and csv files).  
- tVI.csv exports the step number of the experiment (t), the voltage (V) and the total current (I)  
- states.csv exports for each step of the experiment (t) the electrical resistance values of each memristor composing the network.  

### PySpicefunction.ipynb
Pyspice function: calculates the voltage drop at each node of the memristor network using NGSPICE.

### Memristorfunction.ipynb
Individual memristor function. Allows to calculate the resistance variation of each individual memristor and the gap migration for each applied stimulus. It requires as imput the potential difference in each memristor, which is calculated by PySpicefunction.ipynb.

### Analyzing-memristive-arrays_VEOV.ipynb
This program performs an analysis and restructures the previously exported data. It exports several graphs and the file Remnant-resistance-state.csv, where it saves the value of the remaining resistance of the network (i.e. the resistance of the network at those points where the voltage applied to the network is zero). This file is necessary to be able to plot the heat maps using Maps_VEOV_v2. 

### Maps_VEOV_v2.ipynb
This program plots the remaining resistance states (electrical resistance when the external grid signal is zero) for each individual memristor in the grid as a heat map. This program requires the "states.csv" file to plot the maps.   
In order to run Maps_VEOV_v2.ipynb, a folder called /simulations_n/ must be created in the directory. In this folder the "states.csv" file of the experiment to be plotted must be copied, and also inside the /simulations_n/ folder a subfolder /fig/ must be created where the created maps will be saved. Once this is done, you can run the program.  

## Installation of PySPICE for Anaconda 3 on Windows:
To connect a Python code with SPICE open source (the NG is one of them) we use the PySPICE tool.
To install it, start Anaconda 3, open a console (Jupyter QtConsole) and execute the following command:   

*conda install -c conda-forge pyspice*.  

With this instruction both PySPICE and the NGSPICE simulation engine itself are installed.

