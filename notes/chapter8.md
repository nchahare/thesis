# Epithelial Buckling: Transforming Domes into Folds

# Introduction

In biology, epithelial structures come in all the shape and sizes. We could envision all these structures as curved or folded epithelia. Labeling epithelial structures is complicated, which really means folded together. But at the same time, in developmental biology, development, literally means unfolding of organism. In our system, we can generate 3D dimensional epithelia with its inflation. In spirit of complicated development processes, we decide to try folding and unfolding of the domes in our experimental setup. Through understanding the mechanics of the epithelial tissue, we realized that if the dome is depressurized at extreme rates we could deflate the dome into folds. In this chapter, we will discuss the mechanics of epithelial buckling and transforming domes into folds.

# Rapid deflation produces a buckling instability

In the experiments with constant pressure, we found that the dome achieves a steady state through remodeling the cytoskeleton. The original area of the footprint increases to areal strains of more than 100%, which more than twice of the original area. In cyclic stretching, we found that the fast inflation-deflation would accumulate strains through the cycles. Because of our total control over pressures, we decided to subject the tissue to extreme rates of pressure, leaving no time for tissue to relax and cause it to buckle.

The results from computational model, where we could track the digital dome mechanical effect on tissue and cell scale, show that cortical remodeling driven active viscoelastic dissipation allows dome to achieve high strains. The cyclic stretching at fast rates show that the resting area lags behind actual area. They suggest upon fast deflation this discrepancy between actual and resting area could induce negative viscoelastic stress leading to buckling. We observed that the digital domes would inflate and reach the steady state then upon deflating slower than remodeling scale would come down back into a flat monolayer. In contrast, deflation faster than the remodeling timescales we get dome buckling into folds.

In simulations, we found that it is essential to apply negative pressure for undergoing buckling. This only affects the domes deflating fast as the the pressure becomes negative while curvature remaining positive, creating negative stresses. Whereas, the slowly deflating domes reaches zero strain as pressure approaches zero.

To test this experimentally, we decided to systematically probe two factors: first timescale for cytoskeletal remodeling and second deflation rates. We designed the experiments with pressure profile divided in three parts:
1. Linear increase in the pressure from 0 to 200 Pa in 10s
2. Holding constant pressure for different "hold times"
3. Reducing pressure to -50Pa for different "deflation rates"
We chose the hold times and deflation rates considering the timescales associated with actomyosin cytoskeleton.

Table2: 
Hold times: 6s 60s 600s
Deflation rates: 0.2Pa/s 2Pa/s 20Pa/s 200Pa/s

It is worth noting that the buckling events were characterized qualitatively. The assumption we made was that if the curvature of the monolayer remains smooth and without kinks, we would consider it to be not buckling. In some extreme cases where it was difficult for me to say without biasing the data. I asked my colleagues, Thomas Wilson and Tom Golde, to categories the data set. I performed the experiments for all the conditions and quantified the data by tracking fraction of domes buckling.

We witnessed buckling for all the conditions of hold times ranging from 6s to 600s for fastest deflation rate of 200 Pa/s. This confirmed our hypothesis that the tissue undergoing rapid deflation would have to reduce the area and compressive stresses will be introduced causing buckling. On another hand, deflating slowly at rate of 0.2 Pa/s buckling was observed rarely for all the hold times. This shows that the tissue can remodel the cytoskeleton and change the area drastically to not buckle.

As seen before, the longer “hold times” would give cells time to remodel the cytoskeleton and the shorter ones won’t. We learned that the longer hold time resulted in higher strain and more likelihood of buckling even for slower rates. One can see in the simple diagram that the transition as the proportion of buckling domes increases towards the faster deflation rates with longer hold time and decreases with slower deflation rates with a shorter hold time.

We find that the domes for 6s hold time would have smaller strains as compared to 600s hold time. This is consistent with the results from domes subjected to the constant pressure. The strains increase takes time as the dome remodels to balance the active tension with externally applied pressure. However, it is interesting that we observe domes buckling at 6s. In this condition, we wanted to inflate and deflate the dome before it can remodel.  By considering imaging speeds, we chose 6s hold time, but it is still too slow for the remodeling timescales. 

It is worth noting that there was lot of diversity in the buckling patterns seen through a midsection of tissue imaged by line scan method. For some domes the kinks in the folds were minor and in others they were drastic, reminiscent of the buckling modes of the plates.

# Multiscale buckling

The tissue buckling has been obvious in the confocal images. To get the clear look at the shape of the cells, we created a variation of MOLI adapted for light sheet microscopy. In higher resolution 3D images of dome, we can see variety of thicknesses in the domes: thick part are made by nucleus bulging out and very thin parts at cell periphery.

We repeated the same experiments as described previous section, but with rapid deflation and long hold time. On buckling we discovered more features than the tissue scale buckling. We noticed kinks and crimps at the cellular and subcellular scales. On closer inspection, we classified three levels of buckling:

Tissue scale buckling is clearly visible with cells collectively going from uniform curvature to distorted shape. At this level, we see cells deforming at larger scale and at the junctions.

At shorter scales, we noticed individual cells undergoing buckling. The buckling cell double ups around itself with apical side on the top. The length scale at which cell buckles is much shorter than the tissue. It appears as the cell buckles as unit.

In some cases we see buckling at even shorter length scales, we call it subcellular buckling, as the folds in membrane are distinct from the cell level buckling. These are occurring in the thinnest parts of the stretched cells where membrane buckles at much shorter wavelength. Interestingly, these folds occur on the both, apical and basal, sides of the cells.

Typically, in epithelial cells the membrane is tightly attached to the cortex through membrane-cortex attachment proteins like Ezrin, Radixin, Moesin. It is reasonable to believe that the subcellular buckling is due to actin cortex buckling. To confirm this, we decided to image actin cortex while buckling with SPY actin staining. We found that the actin would follow exact shape of the membrane while undergoing buckling.

Even more interesting results for us were to see domes which not buckling at all at tissue scale but would appear to be buckling at cell or subcellular levels.  Also these categories are not so strictly separated, as there were multiple observation of tissue, cell, and subcellular level buckling.

# Generating epithelial folds

After optimizing the buckling conditions, we decided to explore the epithelial folds. While buckling the tissue area is squeezed into a small area. This would produce folds and wrinkles in the monolayer.   When we monitored the base of dome deflating, we saw the tissue making contact with the substrate certain regions first then others. This lead to formation of folds in the places it made the contact last.

We looked at spherical domes of different sizes to see if there is any pattern to these folds. We found that there were broadly three kinds of folding pattern emerging.

1. Accumulation along the periphery
2. Folds in the middle
3. Mixture of both

First, for the domes with the footprint smaller than $10000 \mu m^2$, we observed repeatedly that most of the buckling would create an accumulation around the periphery. When looking at the timelapse, it gave us the impression of a donut-like structure. However, in three-dimensional imaging of the folds, we could see that it was a crescent shaped fold like a croissant. Fold was taller on one side than other. For larger domes with footprint greater than $30000\mu m^2$, there are more instances of  domes forming the network of folds in the middle. We could get multiple folds connecting each other by forming junctions. Finally, for the domes of intermediate size, we have mixture of accumulation and folds. Although, the proportion of the folds along the periphery decreases.

We find the same patterns as experiment when performing the same deflation experiments with digital domes. The larger domes would produce more radial folds and small domes form accumulation of on the side. In the intermediate sizes we have mixture of both.

# Forming predictable folds

We wondered about how the geometry of the dome would affect the pattern formation. As we see with different sizes the buckle pattern changes. The issue with spherical domes buckling is that the patterns, even though beautiful,  cannot be predicted because of the axis-symmetric shape.  We could possibly guide the folding by breaking the symmetry of the domes. 

Using MOLI, we generated ellipsoidal domes of different sizes. We found that these domes would buckle into a fold along the major axis. Smaller area domes would produce similar peripheral accumulation as spherical domes. The larger domes produced a fold in the center along the major axis. This reasserted that only larger domes would produce folds regardless of the shape.

Finally, to create a controlled and more complex fold than a straight line in the middle we decided buckle a dome with a triangular. We expected that the vertices of the triangles could push the buckling along the medians of the triangle. And as expected domes did buckle into forming a Y-shaped network of the fold. When we repeated the triangular and ellipsoidal shapes with digital domes, we found similar patterns.

On imaging the stability of these folded structures, we found that these folds were stable for hours. We could image them more than 12 hours. However, not all folds were alike, some folds would dissipate into the monolayer. Whereas, others would last longer by forming attachments with each other.

This could be a novel of producing folds. We envision tissue engineering possibilities of the MOLI system by just controlling a few mechanical parameters such as geometry and pressure.

# Summary and discussion

We used the device to create domes and then transform them into folds. We characterized the buckling response with respect to actin remodeling timescales. The domes buckle when deflated faster than they can remodel. We found that the buckling occurs at multiple scales starting from tissues then cells to actin cortex. Then we used this system to understand the fold patterns with different shape and size domes. We presented a novel approach of creating folds from pressurized structure. Along with computational model, we unlocked the engineering potential for the dome system to create controlled folds by just controlling geometry and pressure.

As mentioned earlier, the mechanical instabilities are omnipresent in biological systems. In particular, buckling phenomena has been observed by researchers in MDCK epithelial monolayers through compressive stresses applied by growth in confinement or direct application of compression. Charras people show that the epithelial monolayer under compression of more than 35% strain buckles out of plane. Interestingly, they show that the out of plane deformation is recovered through active contractility within tens of seconds. 

However, we are the first to be able to visualize the minute details of the buckling process leading to insights in the behavior of tissue architecture at multiple scales.

Mechanistically, we understand that these results are a consequence of hierarchical nature of the epithelial tissue. There are various components sustaining deformations and forces at different levels. Actin cytoskeleton plays a key role in defining cell and tissue shape at multiple scales. At the same time, cell monolayer can also be thought as assembly of cells with their own surface tension and material properties. Thus, it is expected that a material with different length scales would also buckle at different length scales. If there is a local weakness in a cell or subcellular feature, we could expect it to locally buckle. For instance we only see subcellular level buckling in very thin cells.  This could also explain why we see no buckling at tissue scale but see buckling at cellular or subcellular levels.

Moreover, it is fascinating to think about the short wavelength folds of subcellular buckling. It is essential to point out that the actin buckling is not new to the field. There are minimal models of actin filaments with myosin motors on a lipid membrane, showing the myosin induced contraction leads to actin filaments or shell buckling. In the membrane-actin droplets, researchers show multiple modes in form of buckling and wrinkling depending of the thickness. They found, counter intuitively, thin shells undergoing buckling and thin shells producing wrinkles in the membrane but not actin. It could relate to different modes of  buckling within a cell.

In context of tissue scale buckling, we can understand these results in terms of modes of buckling in thin shells. The rate at which we are deflating these tissues, our computational model suggest that the cortex behaves like a hyperelastic material. If we repeat the same experiment with elastic shells we would get similar results. In literature on thin shell buckling, we find similar aspects where the folds and patterns emerging when different sized shell are buckles.

Intuitively, we can imagine the slenderness, ratio of dome radius to thickness, guiding the different modes of buckling. Thin shell with high slenderness would lead to higher mode of buckling as compared to thicker shell. However, our experiments go further than just understanding the system but show that we program folds by minimally controlling two parameters: geometry and pressure. In non spherical dome, Ariadna saw for ellipsoidal domes the stresses were oriented in along the axes of elliptical footprint. These anisotropic stress could orient the folding in particular direction to generate a programmed fold. Like rectangular footprint could create a mix of fold along the major axis as well as Y junctions on the sides.
































