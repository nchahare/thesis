# edits

# chapter 7

To investigate the active viscoelasticity of epithelia, we conducted simulations that mirrored the experimental conditions. Under constant pressure, the digital domes reached a steady state while undergoing a reduction in cortical thickness as the cells stretched. Consistent with our earlier experimental observations, once the tissue tension was balanced by the applied pressure, the strain reached a stable point (see Figure 1.7).

To derive the constitutive relation within the computational framework, we subjected the digital dome to varying levels of pressure, generating tension-strain curves and steady-state points. The material response of the domes followed the geometric constraint observed in experiments, resulting in a non-monotonous tension-strain curve.

In addition, a quasi-static inflation of the digital dome was performed to assess the model's robustness. The quasi-statically obtained constitutive relation showed consistency with the locus of steady-state tension-strain points under different constant pressure conditions, as shown in Figure 1.7 B. The resulting constitutive curve also demonstrated characteristics similar to those obtained experimentally, including re-stiffening at significant strains attributed to a barrier mechanism.




To interpret these experimental results in the context of the model, we introduced the concept of the resting area, which represents the area of a cell in a monolayer that is in a steady state. The mathematical framework used in the model describes how the cortical surface changes its shape when deformed. This framework maps the initial shape (known as the reference configuration) to its current shape (known as the deformed configuration), with a corresponding metric tensor for each configuration. To capture remodeling of the cortex, a second reference configuration is added with a dynamic metric tensor, where the cortex has relaxed. We could refer to this as the resting frame.

In terms of cell area, the current area is the actual area represented by the deformed configuration. However, the cell could have a resting area different from the actual area, represented by the second reference configuration due to network relaxation.

$$	A_{rest} = \int_{\Gamma_0} \sqrt{|\mathbf{G}|}dS_0, \text{ and } A_{actual} = \int_{\Gamma}dS.
$$

The metric tensor is used to measure distances and angles within the material. When a material is deformed, the distances and angles within the material change, and the metric tensor reflects these changes.

When the tissue is perturbed from steady state, the actual area can change faster than the resting area because of timescales associated with cortex remodeling. Once cell is stretched, the cell dissipates elastic stresses at viscoelastic timescales through remodeling, eventually reaching a steady state, where resting area will be equal to actual area.

This effect of timescales is particularly evident in cyclic stretching experiments. When the cells are probed faster than viscoelastic timescales, they accumulate strains due to an inability to dissipate the elastic stress. On inflation, cells are able to stretch and at viscoelastic timescales change the resting area  


We observed that, for the slowest condition, the resting area in the digital dome almost overlapped with the actual area. This is because the pressure is changing very slowly at a rate of 0.2 Pa/s, allowing the cells sufficient time to remodel and dissipate elastic stresses. Viscoelastic and turnover timescales in simulations are around 10-30s, which means that over a period of 2000s, the dome stretches considerably and returns to original flat state.

However, when pressure is applied rapidly in cycles of 20 seconds, strains accumulate due to insufficient time for cells to dissipate stored elastic energy. The simulations show that the resting area marginally changes relative to the actual area. Notably, creep experiments, where tissue is stretched at constant tension, demonstrate strain accumulation at the visco-active timescale, where both contractility and viscosity play a role.

Interestingly, the simulations indicate that due to active viscoelasticity, there would be a lag between the peak of pressure and the peak of strain. This lag is clearly reflected in the comparison of resting area and actual area, where the delay decreases with increasing pressure rates. The slowest pressure rate results in the least amount of delay, while the fastest pressure rate results in the most delay. Although we can only experimentally observe this at moderate rates. The experimental data from faster cycles is too noisy to observe the lag.

To sum up, the digital dome model explains the material response of epithelial tissue depending on the rate at which pressure is applied. Slower rates allow for cell remodeling and dissipation of elastic stresses, while faster rates result in strain accumulation due to insufficient time for dissipation. This active viscoelastic behavior is the outcome of cortical remodeling.






























