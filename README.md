# Thermodynamics of the Fe-Fe3S system
This is a rewritten version of the thermodynamic code I made with the help of Dr Chis McGuire and Dr Tetsuya Komabayahsi during my time at the University of Edinburgh.
The code was constructed to help us understand the suitability of sulphur as a contaminating element in the Earth's core.
You can find my full thesis at the following link if you're interested in learning more :) https://era.ed.ac.uk/handle/1842/39254 

## Thermodynamic Theory
I've copied here the theory from my thesis. These are the principles around which the code was constructed. In short, if we have a component A of solid phase at a given pressure (P) and temperature (T) condition, we can assess the Gibbs
free enegry of the solid phase and compare it to the liquid phase at the same conditions and assess which is most thermodynamically stable. We can also take the Gibbs free energies of different components, e.g. A and B, and use
mixing laws to assess the stabiliity of different compositions under different conditions. Doing this allows construction of phase diagrams, and deduction of the physical properties of these mixtures at conditions where we
cannot access that information experimentally. 

### Thesis Chapter
#### Theoretical Principles
This chapter concerns the theoretical principles utilised in these works. This
includes chemical thermodynamics and equations of state.
#### 3.1 Chemical Thermodynamics
Chemical thermodynamics is the study of the state of a system at chemical equilibrium
at a given set of pressure, composition, and temperature. The fundamentals
of chemical thermodynamics can be found in numerous textbooks (Callen
and Griffiths, 1987; Keszei, 2012). Here we touch only on those principles that
are relevant to this thesis.

#### 3.1.1 Gibbs Free Energy
The Gibbs free energy (G) of a system is defined as the maximum reversible work
that a thermodynamic system may exhibit at a given pressure, temperature, and
composition. The works presented here at their fundamental level are concerned
with changes in the Gibbs free energy as a result of pressure (P), temperature (T),
and compositional changes (X). G with regards to P and T may be displayed as
a curved plane, which provides all the required information to derive the thermodynamic
parameters needed for these works (Figure 3.1). The classical definition
of the Gibbs free energy is:

G = H - TS (3.1)

Figure 3.1: Schematic of Gibbs-Pressure-Temperature relationship. 

Pressure and Gibbs free energy have positive convex relations. Temperature and Gibbs free energy
have negative relationship. Finding the derivative of pressure and Gibbs free energy
gives the Volume of a system. Finding the derivative of temperature and Gibbs free
energy gives the entropy of a system.
where H is the enthalpy, T is temperature in Kelvin, and S is entropy. Enthalphy
can be descirbed as:

H = U + PV (3.2)

Where U is the internal energy. Entropy is closely associated with the T of a
system, and enthalpy more closely associated with the volume and P.

##### Temperature
Temperature is most simply a measurement of how hot or cold an object is. More
formally, it is a measure of the amount of thermal energy stored within a system.
Temperature is an intensive parameter, meaning it is independent of the size of
a given system and is a differential coefficient of two extensive (size dependent)
variables of a thermodynamic system(Equation 3.3).

T =dU/dS(3.3)

Where T is the temperature given in Kelvin (K), S is the entropy in Joules per
mole (J  mol􀀀1), and U is internal energy in Joules (J). Entropy is the measure
of disorder or chaos in a system. It is closely tied to temperature, as increases or
decreases in temperature have corresponding changes in entropy. These changes
are most easily described as the changes in vibrational energy of the atoms in the
material. In thermodynamics temperature is measured in Kelvin and is described
as absolute, meaning the value of 0 K is universal and therefore no negative values
of temperature are achievable. This means that at 0 K, the entropy of a system
is 0 and the system should theoretically be perfectly ordered. With regards to
Equation 3.1, this defines the most fundamental effect of temperature on the
Gibbs free energy of a system.

From changes in entropy, it is possible to define the heat capacity of a material
or system. Heat capacity is defined as the amount of thermal energy required to
change the temperature of a system by 1 K. Heat capacity is described as one of
the second derivatives of G, and at constant pressure is:
CP = T (dS/dT{_P})  (3.4)

##### Pressure
Pressure is defined as the force exerted on the boundaries of a system. It is
directly linked to the volume of a system; reducing P allows a system to expand,
while increasing P causes it to compress. Pressure is determined on a fundamental
level following:

P = 􀀀@U@V (3.5)

where V is volume in m3. Pressure and volume are closely linked to the enthalpy
of a system. The enthalpy of a system is defined as the sum of the internal energy
of a system (U), and its pressure multiplied by the volume (eqaution 3.2). The
pressure-volume term is in essence the definition of the systems physical dimensions,
expressed as work the system does on the surroundings. This relationship
ties the effect of pressure to the Gibbs free energy of a system (Equation 3.1).

Derivation of G to P gives the volume of a system:

V = @G@P (3.6)

It is therefore possible to calculate the contribution of pressure to the Gibbs free
energy of the system by integration of Equation 3.6 (see Equation 3.9). This
relationship is used extensively in these works, and will be described in more
detail later.

##### Composition
In classical thermodynamics compositional change in a system is generally not
discussed. Its effect on the Gibbs free energy is simply explained, and changes to
the Gibbs free energy of a system through composition (X) changes are dictated
by which components are participating in reactions. Chemical reactions in systems
will tend to move towards the side of the reaction with the lowest Gibbs free
energy, and therefore most stable side until a state of equilibrium is achieved. It
is therefore necessary to understand the effects of composition in terms of equilibrium.
Equilibrium in a thermodynamic system is defined as the condition at
which a system or a group of systems exist where there is no net transfer of energy
or mass between systems or the surroundings. This is the point of minimisation of
the Gibbs free energy, i.e. where its value is lowest. The system can be described
as stable under equilibrium, but should not be viewed as static as reactions will
still be taking place and processes occurring on a microscopic scale with no net
change to the internal energy, or change in the system at a macroscopic scale.
Equilibrium sets limits on the range of stable compositions a system may have at
a given P-T condition. Situations in which true equilibrium is not achieved, but
the system does not continue to evolve to the equilibrium condition are termed
meta-stable. Meta-stable conditions allow the existence of phases at conditions
where they are not thermodynamically stable. An example of a meta-stable phase
would be diamond, which is only formed under extreme pressure but remains stable
at ambient conditions. Meta-stability is often exploited in industrial processes
for generating novel alloys.

It is important to introduce a new quantity in discussing the effects of composition
on the Gibbs free energy, and that is the chemical potential (). Compositional
equilibrium of a system easily identified in the form of  vs X plots (Figures
3.2, 3.3). Chemical potential is simply the change in G of a system through addition
of an increment of component mass to a phase, and the masses of the other
components under fixed P and T. When studying these changes, especially in
simple 2 component systems, pressure and temperature are fixed so that only
contributions from composition are considered. The chemical potential of each
component in a system (A and B in Figures 3.2, 3.3) is equal in all coexisting
phases at equilibrium ( and  in Figure 3.3). This can be easily proven: if the 
of some component is higher in one phase than the other, the excess mass of the
component will shift to the lower  phase bringing the phases into equilibrium,
lowering the overall G of the system to achieve greater stability. Graphically, this
is displayed by the common tangent between the phases in Figure 3.3. Systems
may be composed of numerous phases, but common tangents may only connect
two phases to one another.

Common tangent constructions provide more information than just the equilibrium
composition. They can also be used to delineate stability fields of phases
in a system as a function of composition.

The Gibbs free energy for a two component system can be defined as:

G = (1 􀀀 xB) A + xBB (3.7)

where xB is the proportion of component B in the system, and A and B are
the chemical potentials of A and B under constant P and T. Equation 3.7 can
be expanded by breaking the chemical potentials into standard conditions and
compositionally dependent parts, giving:

G = ((1 􀀀 xB) [o A + RT ln aA] + xB [oB + RT ln aB] (3.8)

where o
x is the chemical potential of the component at standard conditions, and
ax is the activity of the component in the system. The activity is defined as the
effective concentration, i.e. only the portion of the component in the system that
will undergo reaction. The values for activity vary between values of 0 and 1,
and therefore their contributions to the G of the system is always negative. This
is the most basic formulation for mixing liquids in a thermodynamic system, and
the resultant mixture is termed an ideal solution. Other mixing models will be
considered in a later section.

Figure 3.2: Schematic of chemical potential vs. composition for a hypothetical system
of liquid components A and B. The pressure and temperature of the system are fixed,
therefore all changes to G in the system are dictated by composition change, and can
be represented as chemical potential (). This system assumes complete miscibility between
the phases, allowing the existence of only one liquid. The dashed line represents
the linear average of the mixture where only mechanical mixing is assumed, the difference
between this and  of the miscible liquid is given by the equation on the graph.
Point G shows the lowest energy composition of the system, marking the equilibrium
composition of the system.

Figure 3.3: A hypothetical system of components A and B in which two phases of
 and  exist. Each phase has its own curve for G over the compositional ranges
at which they are stable. Intersection of two such curves allows coexistence of the
phases over a certain compositional range. The common tangent shows the equilibrium
compositions for the components A and B where it touches the G-X curves for the  and
 phases. The equilibrium compositions XBand X
B are only positions at which the chemical potentials for B are equal between phases at these P T conditions. Between
these two points, the phases coexist as a mechanical mixture in equilibrium, allowing
crystallisation of  and  phases.


#### 3.1.2 Phase relations

The Gibbs free energy of any phase as a function of P at a given T may be
assessed through the following equation:

GP;T = G1bar;T + Z P1bar VTdP (3.9)

Where G1bar;T is equivalent to the chemical potential of the material at ambient
pressure and the temperature of interest, and VT is the volume at the temperature
of interest. The chemical potential is classically defined as the maximum energy
that can be released or absorbed through changing the number of particles of
each species in the system. Species here means the stoichiometric compounds of
interest. At ambient pressures the Gibbs free energy can be equated to that of
the chemical potential, as the pressure contribution is negligible. The remaining
energy in the system, therefore, is governed by thermal activity. G1bar;T for most
elements can be obtained via metallurgical databases. Dinsdale, 1991 has been
used to provide the required elemental information in this work. The database
provides the information required to calculate chemical potential as a power series
in terms of T:

G = a + bT + cT ln (T) + X dT n (3.10)

where a; b; c and d are coefficients obtained through fitting experimental data,
and n is a set of integers. When utilising these data for calculation of liquid
alloys, consideration of non-ideal mixing behaviour is required.
The second term in Equation 3.9 is less easily obtained. Metallurgical stud
Figure 3.4: Schematic compression curve with integration area shown in red.
ies rarely consider pressure effects on reactions, so the pressure contribution to
G is poorly constrained for most materials. The second term is the inverse of
Equation 3.6, meaning we can use changes in the volume and pressure to give us
the contribution of pressure to GP;T . This information can be obtained through
definition of the thermal equations of state of a material, which shows how pressure
affects the volume and compressibility of a material at elevated temperature.
Once defined, the pressure contribution to the Gibbs free energy is given as the
integration of the compression curve of the material (Figure 3.4).

##### Phase transitions

A phase transition in P-T space is defined as the point at which both phases
either side of the transition are in equilibrium and are stable. In other words:

GA = GA0 (3.11)

Where A and A’ represent different phases. It is possible to calculate any phase
transition of a material based solely on the equations of state parameters and the
chemical potentials of the phases of interest. In the case of these works (Chapter
5), constraining the point dG = 0 for the melting of solid Fe3S allows liquid
equations of state for Fe3S to be constrained.

##### Eutectics

A eutectic system is a system composed of two or more phases, that are soluble
in the liquid phase but immiscible in the solid phase. When the system is heated,
both phases melt simultaneously at a temperature lower than the melting point of
the constituent phases. This melting point is termed the eutectic temperature. At
a given pressure, the composition of the eutectic temperature is always the same
and hence is named the eutectic composition. These relations are most commonly
plotted as temperature vs. composition plots, with the pure end member phases
placed at opposite ends of the X axis and temperature on the Y axis (Figure 3.5).
Figure 3.5: Schematic binary eutectic phase diagram between components of A and B.
TEut and XEut represent the eutectic temperature and composition respectively. Fields
of A and B close to the end members are to display limited solubility of the solid phases
in one another at high concentrations.

Freezing of a liquid in a eutectic system follows the same route each time.
A liquid of some composition above the liquidus is cooled until the liquidus is
intercepted. A small portion of the liquid will begin to crystallise, the composition
of this solid is dictated by the location of the eutectic point relative to the liquid
composition. Whichever side of the eutectic the liquid sits on, the closest end
member will be the first phase to crystallise from the liquid. Upon further cooling
the composition of the remaining liquid evolves following the liquidus curve down
to the eutectic point. At this point, the liquid will be fully crystallised producing
two solid phases in the same ratio of the composition of the initial liquid phases.
Recalling 3.11, we find that the liquidus curves must represent the zero point of
the liquid phase chemical potential and the chemical potential of the liquid phase
coexisting with some of the solid phase. Determining the Gibbs free energies of
the liquid and solid phases, then utilising either ideal or non-ideal mixing models
the liquidus curve may be be calculated for the eutectic by finding the zero point.
The eutectic point cannot be determined from calculating one liquidus curve, so
both are calculated using the Newton method until the crossover point of the
curves is found. This method requires full knowledge of the equations of state of
the phases in the system, as well as their G1barT relations.

Figure 3.6: Schematic binary eutectic diagram displaying the solidification pathway
of a liquid. The red star signifies a composition of Xl
B dropping in temperature until it
hits the liquidus for A+liq. The liquid evolves in composition along the liquidus line as
temperature drops until the eutectic composition is met. The final product is a mixture
of two solids with the same overall composition as Xl
B. Melting works the same way,
but in reverse order.

A simpler method to calculate the liquidus curve requires only the knowledge
of the entropy upon melting of the end member phases, which may be derived
from the melting curve. From Cemic, 2005:
Tliquidus =SB  TmeltB SB 􀀀 RlnX (3.12)

Tliquidus =SA  TmeltA SA 􀀀 Rln(1 􀀀 X) (3.13)

Where Sx is the entropy of melting of the phase at pressure, TmeltB is the
melting temperature of the end member at pressure, and X is the mole fraction
of component B in the system. This method also requires paired equations to
work, but it may be calculated from the melting curves of the end members
alone. It however neglects influences from changes in the constant pressure heat
capacity, and therefore only serves as an estimation of the liquidus.
At a given temperature, the liquidus temperature may also be found considering
the G vs X of the system (Figure 3.7). Under a given temperature, the
intersections between the liquid Gibbs curve and the solid Gibbs curves denotes
the composition at which the transition occurs, along with the common tangent
constructions between the solid and liquid phases. Increases in temperature generally
stabilise the liquid phases, until no common tangent can be constructed
and the liquid is the only phase present. The opposite happens for solid phases,
until the only common tangent is that between the solid phases present.
Binary eutectic systems provide the most light element rich compositions
achievable in hypothetical single contaminant cores. It is required by the change
in density deficit at the inner core boundary that the inner core is enriched in
Fe and the outer core enriched in lighter elements. The density change cannot
be explained by the crystallisation of an Fe-alloy alone, as the density jump is
too high (Li and Fei, 2007). It is required that the liquid composition sits to the
Fe side of the eutectic point. Any compositions containing higher light element
contents will crystallise the solid light element phase instead of Fe, and therefore
not reproduce the observed density jump.

#### 3.1.3 Mixing Models for Liquids
The mixing of liquids is presented in two ways in these works. The simplest
method is ideal mixing, producing ideal or regular solutions. The second more
complex method is non-ideal mixing.

Figure 3.7: Schematic binary eutectic system and how it relates to the Gibbs free
energy curves of the phases in the system. Each phase (; ; and liquid) has its own
curve, the intersection points show the composition of the liquidus curve at a given temperature.
At T1, the liquid curve has the lowest G over all compositions and therefore
is the only phase at this temperature. As temperatures drop between T2 and T4, the
solid phases become lower in G and stabilise while the liquid curve rises and destabilises.
Eventually T drops enough to where only the solid phases can exist, and no common
tangent for the liquid phase can be constructed.

##### Ideal Mixing
Ideal mixing is the simplest way to model the interactions of two phases. The
formulation for an ideal mixture (Equation 3.8) is based only on chemical potentials,
and mole fractions of the components of the system. The model does
not account for variations in the interactions between atoms or molecules. It is
best applied to dilute systems, or those at extreme pressures (Komabayashi et al.,
2019a; Komabayashi, 2021a) where the external force applied override the effect
of interatomic forces. It is often assumed at pressures approaching the Earth’s
inner core boundary that all Fe-light element systems should be totally ideal.
Non-ideal Mixing

While ideal mixing makes no consideration for interactions between phases, nonideal
mixing does. In most real solutions, interatomic forces are considerable
enough to affect the mixing behaviour of the phases. Examples of these forces
would be Van der Waals and Coulomb forces. These interactions are unpredictable,
and study of each system is required to define its non-ideality. There
is no single formulation for a non-ideal mixture, though several methods are
commonly used to describe non-ideal solutions. Non-ideality in a system can be
categorised in one of two ways:

• 1. Interaction forces between differing species (atoms or molecules) are
weaker than between like species
• 2. Interaction forces between like species are weaker than between differing
species

This results in different behaviour in the resulting solutions. Solutions where
forces are weaker between differing species will exhibit immiscibility as the phases
will not mix. The resulting solution will have a higher enthalpy than the component
phases, requiring the reaction of mixing to be endothermic. Solutions where
forces are weaker between like species weaker result in phases that completely mix.
The enthalpy of the mixed phase is lower than that of the components, releasing
energy in the form of heat. Mixing in these systems are therefore exothermic.
The mixing behaviour between Fe and candidate light elements is of significance 
when modelling hypothetical core compositions. It has been assumed that
the mixing behaviour of Fe and light elements under the pressures of the core
should be ideal (Badro et al., 2014). However, non-ideality can persist in binary
systems to significant pressures (Komabayashi, 2014; Pommier et al., 2018). Nonideality
in liquids tends to extend their stability fields to lower temperatures than
ideal liquids. Neglecting non-ideality may lead to inconsistencies in reproducing
experimental data, and give inaccurate estimates on the maximum contents of
light elements in the core.
#### 3.2 Equations of state
When discussing the thermo-elastic properties of the Earth’s core, it is critically
important to have a construct describing the interplay of the state variables of
the core. These variables are most commonly the volume (V) of the system, the
pressure at which the system exists, and the temperature of the system. Relating
these three parameters gives us a "PVT Equation of states (EoS)". Elastic moduli
and seismic wave velocities are easily determined from the EoS of candidate
materials, which allows direct comparison with seismic data of the Earth’s core.
The main purpose of the EoS in Earth science is to deduce parameters such as
the bulk modulus, through fitting of experimental data.
#### 3.2.1 Isothermal Equations of State
There is no definitive EoS that perfectly describes how matter behaves under the
influence of pressure and temperature. There are, therefore, numerous formulations
of EoS, with their origins based on different physical principles. In Earth
science, two groups of EoS are commonly used: (1) those that have their basis in
mechanics and thermodynamics, such as the Birch-Murnaghan EoS, constructed
from general state relations between thermodynamic properties; (2) those that
consider inter-atomic potentials, such as the Vinet EoS, where the repulsive and
attractive forces between atoms dictate changes to the material. In either case,
for most Earth-forming materials the choice of EoS is trivial, as the outcomes are
often very similar for isothermal compression. There are significant differences
in the predicted compression behaviours of materials at extreme temperatures
depending upon the chosen thermal pressure model used. For example, at high
temperatures anharmoic vibrations in the lattice of materials can add to the thermal
pressure. If the choice of thermal pressure model does not account for this
the constructed EoS will be inaccurate. In the these works (Chapter 4), the 3rd
order Birch-Murnaghan EoS was used to derive EoS parameters of solid Fe3S.
#### 3.2.2 Thermal Pressure
Classically, EoS were first defined to constrain PVT relations in gaseous phases.
These EoS often have the contribution of temperature included as standard, as
thermal expansion in gases is pronounced even at small temperature changes.
However, in solid and liquid phases, thermal expansion is comparatively low.
Hence, the formulation for EoS in these phases often includes the thermal contribution
as "thermal pressure", added as a contribution to an isothermal "room
temperature" EoS. In this work, only solid and liquid phases are considered, so
all thermal contributions to the EoS will take the form of this thermal pressure
correction. In Chapter 4, the thermal pressure models assumed for Fe3S are the
Mie-Grüneisen Debye thermal pressure model and the linear KT models. The
Mie-Grüneisen Debye model was adopted as it allows closer consideration of anharmonic
contributions to the thermal pressure, which are difficult to deal with
in the KT model.
