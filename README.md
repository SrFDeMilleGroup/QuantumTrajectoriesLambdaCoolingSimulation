# QuantumTrajectoriesLambdaCoolingSimulation
Code that uses a quantum trajectories approach to simulate Lambda cooling in $^{2}\Sigma$ molecules

# Brief Summary
A brief introduction to the code and how to use it can be found in **QTSimulationQuickWriteup**

Even briefer: This code uses a quantum trajectories approach (see Chapter 6 of https://lukin.physics.harvard.edu/files/lukin/files/physics_285b_lecture_notes.pdf) to simulate \Lambda cooling of molecules with a 'typical' ^{2}\Sigma level structure.  This assumes cooling on the X-->A transition, and that the A state has no hyperfine structure.   I've preloaded options to apply this to SrF, CaF, and CaOH.  I can add others upon request.  

Wavefunctions, velocities, and positions of molecules interacting with the polarization-interference-pattern created by 3 counter-propagating pairs of \sig+/sig- lasers (Here I assume a MOT-like configuration, where, along +x and +y, light is \sigma^{+} and along +z it is \sigma^{-}.  Vice versa for -x,-y, and-z).  The intensity of the lasers (both overall intensity and the ratio between the two coupled states), what pair of states are being "\Lambda" coupled, the detuning (both overall detuning and raman detuning), are all user inputs.

# QTSimulationQuickWriteup

I strongly recommend any user to read this pdf before running simulations.  It explains what the code does (in light detail) and shows some results.

# lambdaCoolingFinalAddCaOH.cpp

The simulation is all contained in this c++ code.  It uses the Armadillo (http://arma.sourceforge.net/download.html) library, which you will need to download if you are planning on running this on your home computer (alternately, most `super-computing' clusters already have this installed, and then you can just load it as a module).  More details are in the **QTSimulationQuickWriteup**.

# testBatch.sbatch

Batch file I've used to compile and submit the simulation to the cluster.  Note the line:

./testVaryCaFSrFNoPathLengthCorrectPol 2.9 $dRaman $satParam 0.9 0 2 0

This runs the executable file created by the compiler (here, testVaryCaFSrFNoPathLengthCorrectPol, but you can change the name of the executable in the g++ compilation line).  This simulation requires 7 inputs:

1) Detuning (here, 2.9).  This is the overall laser detuning (\Delta in figure 1 of **QTSimulationQuickWriteup**)

2) deltaRaman (here $dRaman, which is iterated over in the batch script).  This is the `raman' detuning

(work in progress, finish later)
