# Dynamic material response of epithelial domes

# Introduction

Our motivation in this thesis is two fold: first to create three dimensional epithelia with controlled pressure, and second to study the material response of the tissue to different regimes of tension. The first goal has been achieved through fabrication of monolayer inflator (MOLI) device. We are able to form epithelia domes where cells are stretched for more than 100% of area strain.

Because of the physiological functions of epithelia, tissue has to undergo deformation over a wide range of timescales and magnitudes. Same for pressure, it is recorded that the luminal pressure in blastocysts doubles over its development leading changes in cortical tension and strain. MDCK dome system is a perfect system where we get to see the interplay between cell strain, tension, pressure. Latorre et al observed wide range of the pressure throughout evolution of the dome; and cells go through range of deformation including displaying active-superelastic behavior. However, the control is applied only on the footprint of the domes. In this chapter, we would use the MOLI system to actually subject tissues to range of strain and tensions.

# Measurement of dome mechanics

To measure kinematics of the domes, we analyzed midsection of the domes assuming symmetry of spherical caps. We measure the height $h$ and base radius $a$. This allows us to calculate radius of curvature $R$ using trigonometry.
$$ R = \frac{h^2 + a^2}{2h} $$
This also allows us to compute tension $\sigma$ given by Laplace's law. 
$$\sigma = \frac{\Delta PR }{2}$$
For dome strain, we use areal strain measure which is strain computed on basis of surface area. We compare dome surface area to the area of footprint.
$$ \epsilon = \frac{A_{dome } - A_{footprint}}{A_{footprint}} $$
$$ \epsilon = \frac{\pi(h^2 + a^2) - \pi a^2}{\pi a^2} = \frac{h^2}{a^2}$$
Using line scan method of imagining domes for time-lapse, we get large amount frames for analysis of height and radius of curvature. Thus, we use kymographs to of the top section of the dome. Kymographs are the images with cross section of dome top with respect to time. Using image processing MATLAB code, we get the location of maximum intensity value for particular time in the graph, to obtain the time evolution height of dome. Same is done for the base radius too. The kymograph of base radius allows us to keep track of the delamination. Because delamination would change the value of strain.

# Epithelial domes at constant pressure

First we decided to study behavior of domes subjected to the constant pressure. We tried inflating domes at different pressures. But in experiments, as mentioned earlier, we noticed few to none of the domes forming at lower pressure than $50-100 Pa$. After optimizing for different pressures  we settled on using $200Pa$ which allowed domes to form and not delaminate.

We found that the areal strain of the dome would increase in first $3-5min$ of the pressure application. Later it would reach a plateau in the strain till $5-10 min$. Even though the dome to dome variability is large in the strains ranging from 50% to 300 %. This stabilization in strain indicates some kind of steady state achieved by the tissue. 

On closer examination of tension - strain curve of these domes, we see a peculiar curve. The tension is non-monotonously changing with respect to strain. It resembles a swish symbol of "Nike". The tension is extremely high for low strains and then it is reduced to minimum around areal  strain of one, where dome is a perfect hemisphere. The dome increases the tension later but the slope is relatively gentle as compared to steep decline in tension for low  strains.

This kind of material response would be strange for typical material undergoing uniaxial stretching. However, in our case, the explanation of the curve lies in the geometric constraint imposed by the dome system and Laplace law. As the dome tension is dependent on radius of curvature, as the dome inflates radius of curvature starts out very high producing higher tension and it reduces to minimum with hemispherical shape and then increases again. Radius of curvature, areal strain and tension at inherently interconnected, such that at a constant pressure we can write the expression of the curve.

$$ R = \frac{h^2 + a^2}{2h} $$
$$ R = \frac{h^2/a^2 - 1}{2h/a^2} $$
$$ R = a\frac{\epsilon^2 - 1}{2\sqrt{\epsilon}} $$
$$ \sigma = \frac{Pa}{4} \frac{\epsilon^2 - 1}{\sqrt{\epsilon}}$$
In experiments, if we normalize the tension with the base radius we have all the domes collapsing on one curve corresponding to a specific pressure. We  would call it 'isobaric' curve.

In terms of physics, we understand that when the step pressure is applied the dome suddenly inflates and has  to undergo non-steady state out of equilibrium stresses. It is very clear that this curve does not represent the quasi static constitutive relation of the epithelia tissue.

# Constitutive relation of epithelia

To obtain the real constitutive relation, ideally we should quasi-statically increase strain or tension. In our system we can only control the pressure. Increasing pressure slowly doesn't work with domes as they don't delaminate at low pressures and if they do they are in non-steady state regime where they inflate rapidly to higher strains. The rational choice for us was to capture steady state corresponding to different pressures.

We applied $200 Pa$ pressure for $5min$ till the dome achieves steady state. Then we reduce the pressure by $20Pa$ and wait for the domes to reach steady state again. We continue repeating this step till dome has been deflated totally. The tension strain curves this way captured parts of isobarics as the dome passes through different pressure steady states.   

We obtained a constitutive relation which shows linear increase in the tension with increase in strain for lower strains. However, for the large strains the tension seems to be achieving a plateau consistent with earlier MDCK dome studies. It is important to note that the dome to dome variability is large. Also the tension recorded of $4.5mN/m$ are of the same order of magnitude as previous studies.                                                        

# Dynamics of the epithelia domes

To probe the dynamic material response of the domes, we performed cyclic stretching experiments with the domes. We subjected domes to triangular wave of pressure with magnitude of $200Pa$ at three different timescales. Considering the literature on cell remodeling and experimental conditions, we chose 20s, 266s, and 2000s cycles.

Table1: 
Time period: 6s 60s 600s
Rates: 0.2Pa/s 1.5Pa/s 20Pa/s

For fastest cycles, we observed domes progressively stretching more as the cycles progresses till it reaches a steady state. We performed experiment for 1200s (60 cycles) and noticed that the domes would accumulate the strain progressively. It would stretch while loading and unstretch while unloading but it would not go to zero strain after first few cycles. In last cycles, we see that the dome oscillates between two state of strains.

Similar response was seen in the moderate cycles, where domes are stretched for 5 cycles each of 266s. The strain would accumulate in first cycle itself with strains reaching higher than the fast case. Also, after few cycles, it appears to have reached steady state.

Finally, for the slowest of all, 2000s cycles, we had difficult for forming domes at lower pressure. As described earlier, the domes would not detach till they reach critical pressure of 100-150Pa and then inflate rapidly to really high strains of 200-300%. However, it was clearly visible that the strains were not accumulating. And there was no difference in the maximum strains achieved in both cycles showing that at this timescale the steady state is reached immediately.

One puzzling things we saw that in some cases of slow and moderately fast cycles had delayed peak in strain when compared to maximum point of pressure, indicating that when the pressure is reducing dome continues to inflate and increase the strain.

# Active gel tissue model

In parallel, to complement the understanding of the experiments, we worked closely with Adam Ouzeri to develop an computational framework. The general understanding of epithelial mechanics is that the actin cortex viscoelasticity plays a critical role in sustaining deformations at the timescale of seconds to minutes. Adam Ouzeri developed a theoretical framework that bridges active gel models of actomyosin cortex and 3D vertex models at tissue scales. In this model, each cell is represented by a active gel surface accounting for physical aspects of the  cortex. We could assemble a tissue which is made with a collection of these active gel surfaces.

In the model, the dynamics of the system is formulated through balance of different potentials representing different active internal or external forces and dissipation.

Briefly, the model incorporates the molecular dynamics of the actin filament network along with myosin and crosslinker proteins through following components:

1. **Cortical thickness:**  Here, the cell cortex is modeled as a hyperelastic membrane with cortical thickness ($\rho_R$). The deformation kinematics of this model is defined by mapping $\varphi$ a cortical patch from a reference configuration $\Gamma_0$ to deformed configuration $\Gamma$ with metric tensor $G_0$ to $g$ respectively. As the material is dynamic, constituents of the network constantly changing, the reference configuration has to be dynamic. For this reason, there is a second reference  configuration with its metric tensor, becomes a dynamic variable $G$, similar to literature on nonlinear viscoelasticity.
   To summarize, the cortical thickness in reference configuration will change with the mapping change represented by Jacobian $J_R$. 
   $$ \rho_R(\xi, t) = \rho(x,t)J_R(\xi,t) $$
1. **Network elasticity:** This potential accounts for the free energy of the system undergoing deformation. The potential is dependent on the difference between in-plane strain ($C$) and the metric ($G$) written in format of hyperelastic potential ($W$). By using Neo-Hookean elastic potential, $W$ will depend on two Lamé parameter, $\lambda$ and $\mu$  $$\mathcal{F} = \int_{\Gamma_R} \rho_R \ W(\mathbf{C,G})dS_R$$
2. **Dissipation:** The actomyosin network is known to remodel under tension, thus the released elastic energy can be accounted dissipation potential. It depends on a coefficient $\eta$ equivalent to bulk viscosity, cortical thickness, and rate of metric tensor given by $\dot{G}$
   $$\mathcal{D} = \int_{\Gamma_R} \frac{\eta}{2}\ \rho_R \ \mathbf{\dot{G}}:\mathbf{\dot{G}} \ dS_R $$
3. **Active contractility:** Ultimately, this model is an active gel, the active part is included through an active power potential which adds energy in the system.  It is dependent on the cortical tension and the rate of deformation tensor. The cortical tension is a active tension component of the network which is proportional to cortical thickness. $$ \gamma(\rho) =  \rho \xi$$ $$ \mathcal{P} =  \int_{\Gamma} \gamma : \mathbf{d}  \ dS$$4. **Turnover dynamics:** The turnover of the cortex is generalized into mass balance law, where network is constantly polymerizing and depolymerizing with cytosolic components. Here, it is assumed that there is a steady state cortical thickness.
$$ \dot{\rho} + \rho \ tr(\mathbf{d}) = k_p\ C - k_d\ \rho $$

The governing equations will be resulting from minimization of the Rayleighian defined as following.

$$ \mathcal{R = \frac{dF}{dt} - D + P + P_e}$$
Here, extra $P_e$ is a potential added because of the external forces and tractions. It was assumed that the cell volume is conserved through the deformations. Also, a mechanical barrier was implemented to limit strains beyond a threshold. This was introduced by adding re-stiffening at large strains. Physiologically, there are number of reasons by which cells would not stretch perpetually, like activation of the intermediate filaments or compression of the nucleus. 

Broadly, we get three timescales associated with the model: Turnover time ($1/k_d$), viscoelastic time ($\eta / \lambda$), and viscoactive time ($\eta / \xi$). The model shows that the system behaves like an active viscoelastic fluid, at shorter timescales it behaves like a hyperelastic material and at longer timescales as viscoelastic material.

Adam Ouzeri could implement this model in our system, where he would create a digital twin of the monolayer with a cell monolayer. He could also, have non adhesive regions which on application of pressure would inflate in domes similar to our experiments.

# Active viscoelasticity of the epithelia

On repeating the simulations in conditions of the experiment, we could understand the mechanics of the system. The digital domes on inflation with constant pressure would inflate and achieve a steady state too. Along with stretching of cell the cortical thickness decreases. However, on holding constant pressure, after some time the strain is stabilized when tissue tension is balanced by the forces we are applying in this case is pressure

To evaluate the constitutive relation given by the model, digital dome was inflated with different pressures to get isobaric curves and steady state points. Alongside, a digital dome was inflated quasi-statically, this is not feasible in the experiment. The goal was to see the robustness of the model. We found that constitutive relation obtained quasi-statically was consistent with the locus of the steady state point in isobarics. The constitutive curve shows similar characteristics as experiments with clear re-stiffening at large strains which we introduce as a barrier mechanism.

We can interpret these results through the concept of the resting area, It is an area of cell in a monolayer, where it is in steady state. When perturbed from this state the actual area changes faster than the resting area because of the viscoelastic behavior of the tissue. The cell is able to dissipate the elastic stresses at the viscoelastic timescales through remodeling, thus reaching steady state.

This effect of these timescales are more evident in the case of cyclic stretching experiments. We can see clearly that the cells, when probed faster than viscoelastic timescales, are accumulating strains because they cannot dissipate the elastic stress. However, in case of slower stretching the elastic stresses are able to be dissipated with increasing area. 

In digital dome, we can observe that in the last two cycles that the resting area is almost overlapping the actual area for the slowest condition. Because in this condition, we are changing pressure so slowly at a rate of 0.2 Pa/s that cells can remodel and dissipate the elastic stresses. The viscoelastic and turnover timescales are around 10-30s. So over the period of 1000s dome stretch a lot.

On contrary, we see the other side where pressure is applied faster in cycles of 20s, we see that the strains accumulate because there is not enough time for cells to dissipate stored elastic energy. The simulations show that the resting area marginally changes relative to the actual area. It is worth noting that the simulations of creep experiments, where tissue is stretch at constant tension, show strain accumulation at visco-active timescale, where the contractility and viscosity both act.

# Summary and discussion

In this work, we probed the mechanics of the epithelial tissue by applying pressure at different rates. First, we found that at application of step constant pressure of 200Pa domes dynamically inflate and achieve a steady state in strain. Because of the spherical geometry we found a non-monotonous tension-strain curve in response to constant pressure. However, the true tension-strain curve revealed linearly increasing tension with respect to strains for lower values, but at higher strains the tension seems to be independent of the strains. Second, we show that the domes when probed with fast changing pressure increase and  accumulate strain through the cycles. And reach the steady state in later cycles. However, if stretched slowly the domes stretch to high strains and do not accumulate strains.

We understood the epithelial tissue behavior through active viscoelastic fluid model. Through experimental and computational framework, we could probe the time dependent response of tissue to pressure. We could show that the response of the domes to cyclic pressure is dependent on active viscoelasticity.

The tissue stretches to balance the tissue tension with externally applied pressure timescale and reaches steady state strain through actively remodeling  the cortex. The studies with digital domes show that there are different timescales playing a role together to produce the response of domes to pressure. 

We could understand the model results in terms of multidimensional maxwell model. Classical maxwell model is made up of a spring and a dashpot representing elastic and viscous element. In this case, we can imagine a similar model with two branches: one with spring and dashpot; second with an active spring. If the stretching is done slowly the elastic component (spring) will not stretch only the dash pot would stretch. In other way if we stretch too fast the the viscous component doesn't move only spring deforms. The interplay of cortical turnover, crosslinkers, and the network reorganization allows for large deformations and rapid shape changes.

In past, researcher have looked at the system in a similar fashion where epithelial tissue was modelled by using viscoelastic models of springs and dashpots. A particularly interesting model is done by Khalilgharibi 2019, which  characterizes the response of suspended monolayer to stretch and shows that the dynamics is similar to that of single cell because of the role of actomyosin cortex. They use a model with two springs in parallel, one of which can change its length dynamically. This explains the relaxation of the monolayer, the active contractility of the cortex changes the resting length of the active spring in the model. 

Another study, found that the viscoelastic dissipation could explain the shortening or elongation of the cell junctions in drosophila embryo. They show that the dissipation occurs at the minute timescale at the same timescale as myosin pulses. It is also interesting that they find the actin turnover playing a key role in this dissipation.

There are very few in vitro techniques which can apply tensions and strains on suspended cells. It is critical to understand that the adherent monolayers behave differently than the suspended ones. The matrix supporting the tissue plays a great mechanical role, in providing extra stiffness and also altering the cytoskeletal structure of the cells. However, in this thesis we focus only on actin cortex and the short timescale (minutes).

The actin remodeling timescales are in order of tens of seconds. In our system at this timescales we do not observe any cellular rearrangement or division (very rarely). One of the reason that we didn't perform long term experiments is because of the suspected involvement of the other cytoskeletal components such as intermediate filaments.

In Latorre el al, they observed the activation of intermediate filaments in extremely stretched cells (>300%), which cause re-stiffening and rescues cell from stretching too much. This motivated the form of strain limiting mechanism imposed in the model. However, in our experiments, we do not see any indication of the superelasticity all the cells get super-stretched at the same time.





























