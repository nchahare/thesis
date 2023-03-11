# Microfluidic device for generating 3D epithelia
# Introduction

To create three-dimensional epithelial structures in vitro from planar epithelial monolayers, we chose to begin with already existing system of epithelial domes developed by Ernest Latorre and improved Ariadna Marin. In this system, Madin-Darby canine kidney (MDCK) cell monolayer is seeded on substrate which is patterned with circular non adhesive regions. The cells invade these non adhesive regions and form a cohesive monolayer everywhere in 24 to 48 hours. Due to the tendency of these cells to actively pump ions in apical to basal direction, the cells delaminate from the impermeable substrate, like glass or soft PDMS gel, to form a spherical cap structure in the circular patterns, called epithelial domes. Latorre and Marin studies show that they could form variety of the structures of controlled shape and size, ranging from circular to rectangular shaped structures.

At the same time, the system enabled the use of 3D traction force microscopy, which allows for measurement of pressure. It utilizes the deformation of the soft PDMS gel embedded with beads to characterize the forces and pressures applied by the cells on substrate. It is ingenious way of measuring pressure as compared to the past method of puncturing the epithelial domes with a microneedle. This allowed for characterization of rheology of epithelia and revealed interesting material properties such as superelasticity of cells while stretching. 

However, the process of forming epithelial domes is dependent on ion pumping mechanism of the domes. We can call them spontaneous domes. Thus, the timescales for the dome stretching are not controlled. The process could be accelerated marginally by few hours through use of drugs like Forskolin, which can activate transepithelial channels of NA+/K+/Cl-. However to build the epithelial structure and control it physically requires pressure control.
# Monolayer inflator

Drawing upon the inspiration from organ on chip microfluidic devices, we thought they would be perfect system for controlling pressure, cell culture, and enable us to image at high resolution.  For example, lungs-on-chip device which is a two layers separated with a porous membrane with the channel in top layer for epithelia and another one for endothelia. This is all assembled on a thin glass which allows for high quality imaging.

Therefore, we conceived the idea of monolayer inflator device, where we will use two layer microfluidic channel which will have one side for epithelial monolayer and another on for application of the pressure. The epithelial monolayer side will be micropatterned with protein with non/less-adhesive regions for dome formation. We reasoned that cells will attach everywhere even in less adhesive region. When applying pressure the cells will delaminate from the weakest point of adhesion and form a dome.

We decided use the classical PDMS material for building the microfluidic chip because of ease of use. We attempted making devices from plastic stickers and photopolymerizable glue, but they were unsuccessful and had issues due to leakage or lack of bio-compatibility.

# Fabrication of the device

The structure of the device is in four layers: glass, bottom channel, porous membrane, and top channel. All layers bonded to each other by using ozone plasma activation.

All the device has to be mounted on a thin glass enabling high quality imaging. There are options for using thicker glass slides but for measurement of the curvature of domes, or monitoring cell stretching would require thinner glass of number 1.5.

For the same reason, the bottom channel has to be thin enough to make it as close as possible. This is due to the working distance of most of the confocal microscope objectives. As it is typically between $200\mu m$ to $1000 \mu m$. We chose to fabricate this layer for $100 \mu m$ such that it is thick enough to handle manually but not too thin too cause microfluidic problems of pressure and flow. We used spin coating method to fabricate thin PDMS layer and then used a desktop cutting machine to cut the channel out of it. 

Primary purpose of the porous membrane is allow for pressure application and not let cells pass through from cell channel to pressure channel. We started with $10\mu m$ membrane considering the literature. We tried to use PDMS  $100 \mu m$ thin layer with $10\mu m$ pores, but the microfabrication using photolithography was unsuccessful. We were producing $10\mu m$ pillars with $100 \mu m$ height the aspect ratio was too high for use to get upright domes. Thus, we decided use plastic (PET) membranes with $10\mu m$ pores. The thin ($10\mu m$ thick) plastic sheets, very easy to handle, but the bonding with PDMS was not very sturdy there were bonding failures or leakages because membrane wrinkling.

Later, we decided to attach the PDMS thin layer to a small piece of membrane. The  middle PDMS thin layer will have a $1.2 mm$ hole exposing the membrane to pressure. We chose this dimension because it is approximately the size of the field of view of 10X objective.

The top channel was chosen to be a big block of $5mm$ thickness with a channel of $1mm$ thickness engraved in it. The thickness of this was chosen in an ad hoc way. The only consideration was that the block has to be thick enough to be able to plug in tubing for application of pressure. Because the dimensions were so big we could use a 3D printer to create a mold with a channel. The way we construct the device, there are two channels crossing each other perpendicularly. Therefore we needed to add 4 inlets in the big block. Two for inlets for bottom channel and other two to seed cells.

We bond all these layers in two steps with ozone plasma cleaner. First we bond glass to bottom channel and simultaneously middle layer to top channel. After these are bonded, we bond them to each other with membrane sandwiched in the middle.

# Protein patterning and inverted cell culture

After few trials, we immediately realize that the whole device has to be contained in petri because of the cell culture medium. When we put the glass slide in a larger petri dish. The liquid would go underneath the glass, any leakages during pressure application would cause spillage in microscope. Thus, we designed all the setup to be fitting in a glass bottomed dish.

In case of spontaneous domes, the domes were seeded on a soft PDMS gel in a glass bottomed dish. Thus, the top surface is exposed to any chemical treatment including micro-contact printing, where a PDMS block with a topography is put in contact with surface to pattern adhesion proteins. Later, to have more control and flexibility of patterning proteins, PRIMO technique was used. This uses an inverted microscope to etch protein patterns in the substrate. 

For our setup, it was impossible to use micro-contact printing because the whole device is sealed and bonded. Thus, we decided to use PRIMO technique. This technique was optimized for glass and soft PDMS substrates. Thus, we had to optimize the technique for our setup with plastic substrate, which involved increasing laser power and protein concentration. In the end, we had successful protein patterning. 

We had to optimize the cell seeding too, in other setup cells can just be seeded in a dish. However, in the channel, the cell seeding required high concentration of cells  compared to typical spontaneous dome experiment. We would seed $30\times 10^6$ cells/ml for one hour and then wash away the cells which didn't attach within one hour. 

In early experiments, we would have to cells attached to the surface and protein patterns, but on application of pressure there were very few events dome formation. Another thing was that the quality of the imaging was terrible, we were imaging through the porous membrane. The domes in the top channel would have cells further away from the microscope objective. Upon closer look we noticed cells were filtering through the membrane from top to bottom and protein coating was better on the bottom channel side than the top.

To prevent cells crossing the membrane, we decided to use membrane of smaller pore size like $400nm$. However, imaging green channel $488nm$ was impossible through $400nm$ pores. Here, we decide to change the side of seeding cells from top to bottom. This improved two things. First, imaging would be better as the cells and dome would be closer to objective. Second, cells would be seeded on the good side of the protein pattern.

We call it "upside down" cell culture, where upon seeding cells in bottom channel we would flip the device immediately to make sure cells are attached on the membrane not the glass. We have to wash the channel thoroughly, otherwise cells might attach on the glass which also obstruct the imagine of the domes.

Even with these improvements, the ultimate challenge was to make sure cell monolayer cover the non adhesive regions. To resolve this issue, we had to increase the protein concentration in these regions so that cells could attach there. The cells would be attached to these regions will be attached weakly and would detach there first to form a dome.

# Pressure control

After optimization of protein patterning, cell culture conditions, and confocal microscopy, we dealt with pressure control. The previous studies showed that the pressure under the dome is around $100Pa$. The idea for us was to use hydrostatic as the pressure required to form dome is so low, $100Pa$ is $1cm$ of water column.

In early trials, I was using pipette tips to apply pressure. One side pipette tip would be blocked and other was used to apply pressure by adjusting the height of liquid. However, the pipette tips are not the best because they are prone to bubbles and also if there's a leak the media just flows out. Later, we used Polytetrafluoroethylene tubing connected to a $15ml$ tube. We could match the height of the device with the height of air-liquid interface in the tube. This means that there is a zero pressure on the monolayer. Upon increasing the height of the tube by $2cm$ we would apply $200Pa$ pressure on the monolayer causing it to delaminate and form domes.

With tubing, we have to be attentive to the cavitation or bubbles getting trapped in the cell channel. To ameliorate the bubble issues, we would put the media in vacuum chamber. It would get rid of nascent bubbles which get bigger with time. Also during inserting the tubing, we could easily introduce bubbles again. To solve this, we use the two inlets for each channel by flushing the fresh media from the reservoir to fill up the tube without the bubbles and remove any pre-existing bubbles. 

We used an automatic translation stage which can be programmed to lift the reservoir. We measure the pressure by keeping track of the height of the stage and the zero pressure position. With this stage, we could apply pressure in the range of $0\rightarrow 1500Pa$. Although, by setting it lower we could even apply negative pressure. For typical experiments done for this thesis, we used the range of $-200\rightarrow 1300Pa$.

# Imaging the epithelial domes

Finally, we were able to form domes according to the pattern and control pressure at will. Domes would not inflate right away as they have to detach from the porous membrane. They would delaminate at pressures $50-100Pa$ then we could image the dome in confocal microscopy. We would use 40x objective to image a dome with membrane marked in $488nm$ channel and protein pattern in $644nm$. Labeled adhesion protein made it easier for us to track and anticipate the formation of the domes. The confocal microscopy stack of $100 \mu m$ tall dome with step size of $0.5\mu m$ would take $5min$. This is much slower than we can actually deform the dome by changing pressure. At first, to characterize the epithelial mechanics, we were mainly interested in spherical domes at constant pressure. We could monitor pressure, cell shape, and tissue curvature easily, enabling us to utilize the Laplace's law to calculate tension.

In previous studies, the domes were shown to be dynamic but the dynamics was slow and domes could be recorded at much slower rate of $5min$. In our case, the domes could be inflated and deflated in matters of seconds. We could monitor them by looking at the base of the dome, where monolayer would come in and out of the view. This would not be enough to quantitatively track the state of the dome.

For the studying rheology, it would be of our interest to be able monitor dynamic response of the domes at faster pressure rates or shorter timescales. In this case, we would only be interested in the dynamics of the dome strain and curvature. Due to its symmetry, we could image only the mid section of the dome and get all the information needed to characterize the material response of the dome.

Using the line scanning mode of a Zeiss Airy Scan Microscope, we could selectively image a single line of pixel across the midsection of the dome and take a confocal z-stack along the height of the dome. This will give us a cross-section of the dome in a fraction of the time of normal stack. Along with piezo stage movement enabled, we were able to image $100 \mu m$ tall dome within $4s$. We could even track the dome height evolution through kymograph of the central part of the dome. However, it is important to note that this form of imaging is useful to keep track of the dome strain and curvature, but the quality is of cells imaged is quite low. In some cases, where the fluorescent expression of cells on the top of the domes is not adequate, we have much noisy data.

# Light-sheet MOLI

Later in my PhD, for observing cellular or sub-cellular changes, we could utilize the light sheet microscope. The microscope in our lab, has two immersion-upright objectives at 45 degrees to the horizontal plane. With our expertise at fabricating devices, we were able to design new setup which would have cells and porous membrane exposed to the top for imaging.

We decided to invert the normal MOLI device and simplify the setup for fabrication. For this, we needed a pressure channel and middle layer with hole and porous membrane. The device had to be thick enough to plug in the tubing. The whole device and channels are large so we could fabricate the mold for this using normal 3D printer. We created a ridge-like protrusion so that pressure channel and hole of seeding cells is manufactured in one go. The bonding of the device was done by gluing the device to a microscope slide with unpolymerized PDMS. We were able to primo pattern the device by flipping it upside down. Seeding cells in this setup is easier as the cell seeding part is exposed. 

As expected, we were able to apply pressure with the same system as before and form domes. We could see the features which were impossible to see in other imaging strategies.

# Summary and Discussion

We have developed a microfluidic chip to form 3D curved epithelia. It is a multilevel device, which has two layers separated by a porous membrane. We can seed cells on the membrane 'upside down' way in the bottom channel, so that when dome forms it is closer to the microscope objective. The pressure in this system is applied  using hydrostatic pressure by changing the height of the reservoir. This experimental setup enabled us to control pressure under the dome dynamically, and obtain high quality confocal images. We also developed imaging strategies to capture dynamics of these 3D structures faster using line scanning mode of confocal microscope or light sheet microscope.

It is worth acknowledging that even though the method of forming 3D epithelia described here feels obvious and easy, it is not. We had to go through many iterations of this device and many other methods we tried and failed.

We formed the domes and were able to monitor cells and tissue behavior. The pressure, tension, and curvature could be measured by applying Laplace law for spherical cap domes. As shown in previous studies, the most interesting part of the system is that the complex material such as epithelial tissue to maintain mechanical equilibrium has to adopt a spherical cap shape for circular footprint. This uniform curvature and pressure implies uniform tension, for this we don't even need material properties of the tissue. However, in case of the non-spherical geometry, there would be anisotropic stresses which would require computational model to solve an inverse problem to go from geometry to forces.

The geometry of the domes is controlled through the protein pattern. But it could delaminate further too. This has been shown in spontaneous domes where the researchers found that the most domes had circular footprint. Also, in case of the domes which were instructed to form around a sharp corner would blunt itself with delamination. We would have to keep this in mind while creating particular geometry.

There is an interplay between tissue tension and adhesion forces. As cell-cell junctions are much stronger than cell-substrate adhesion, if we consider that the tension exceeds the adhesion forces at the base of the dome it would lead to detachment and delamination of the domes.

Also, another aspect to think about is that we have created unintentionally a peeling system, where we are able to see tissue being peeled off from the substrate. and if the dome remains spherical, we could even calculate forces required to break cell-substrate adhesion and identify the role of the molecular components of focal adhesion. However, we are more interested in learning more about the mechanics of epithelial tissue under controlled pressure.
