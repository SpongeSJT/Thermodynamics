# Thermodynamics of the Fe-Fe3S system
This is a rewritten version of the thermodynamic code I made with the help of Dr Chis McGuire and Dr Tetsuya Komabayahsi during my time at the University of Edinburgh.
The code was constructed to help us understand the suitability of sulphur as a contaminating element in the Earth's core.
You can find my full thesis at the following link if you're interested in learning more :) https://era.ed.ac.uk/handle/1842/39254 

## Thermodynamic Theory
I've copied here the theory from my thesis. These are the principles around which the code was constructed. In short, if we have a component A of solid phase at a given pressure (P) and temperature (T) condition, we can assess the Gibbs
free enegry of the solid phase and compare it to the liquid phase at the same conditions and assess which is most thermodynamically stable. We can also take the Gibbs free energies of different components, e.g. A and B, and use
mixing laws to assess the stabiliity of different compositions under different conditions. Doing this allows construction of phase diagrams, and deduction of the physical properties of these mixtures at conditions where we
cannot access that information experimentally. 
