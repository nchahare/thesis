---
author: Nimesh Ramesh Chahare
title: Mechanics of inflated epithelia
---

## Abstract

Epithelial sheets form specialized 3D structures suited to their
physiological roles, such as branched alveoli in the lungs, tubes in the
kidney, and villi in the intestine. To generate and maintain these
structures, epithelia must undergo complex 3D deformations across length
and time scales. How epithelial shape arises from active stresses,
viscoelasticity, and luminal pressure remains poorly understood. To
address this question, here we developed a microfluidic setup and a
digital twin to engineer 3D epithelial tissues with controlled shape and
pressure. In the experimental setup, an epithelial monolayer is grown on
a porous surface with circular low adhesion zones (footprint). On
applying hydrostatic pressure, the monolayer delaminates into a
spherical cap (dome) from the circular footprint. This simple shape
allows us to calculate epithelial tension using Laplace's law. Through
this approach, we subject MDCK epithelial cells to a range of lumen
pressures at different rates and hence probe the relation between strain
and tension in different regimes, while computationally tracking actin
dynamics and their mechanical effect at the tissue scale. Slow pressure
changes relative to the timescales of actin dynamics allow the tissue to
accommodate large strain variations. However, under sudden pressure
reductions, the tissue develops buckling patterns and folds with
different degrees of symmetry-breaking to store excess tissue area.
These insights from experiments and the digital twin allow us to pattern
epithelial folds by rationally directed buckling. Our study establishes
a new approach for engineering epithelial morphogenetic events.

# Part I: Introduction {#part-i-introduction-1}

The central focus of this thesis is the epithelial tissue monolayer.
From the perspective of a mechanical engineer, these monolayers are
endlessly fascinating. They are shape-changing, self-healing, and
continuously deforming or jamming depending on the requirement (xi2018).
They are the most basic system in terms of developing a physical
understanding the biological morphogenesis. Epithelia are everywhere:
covering all our bodies and lining body cavities and organs. Epithelial
monolayers adopt a range of shapes from simple spherical blastocysts to
highly branched and folded lungs. These shapes are developed and
maintained through constant renewal and adaptation. In this work, we
have explored the physical principles behind the epithelial shape by
combining theory and experimentation with simple epithelial monolayers.

The chapters in this part are to be a primer for all the topics relevant
to my PhD. Starting with a brief introduction to the epithelial tissue
itself and its key components. Subsequently, the role of mechanics in
morphogenesis, and the approaches to modeling these tissues. Finally, I
will conclude with the emerging field of "bottom-up" morphogenesis,
where researchers are reconstructing biological systems from scratch.

## Epithelial Layers {#epithelial-layers-1}

### Introduction

> Figure: The Anatomy Lesson of Dr. Frederik Ruysch, 1670 by Adriaen
> Backer

A Dutch botanist, Frederick Ruysch, in the early eighteenth century
coined the term 'epithelia' to describe the tissue he found while
dissecting the lips of a cadaver, combining Greek roots '*epi*' for the
top and '*thele*' for a nipple[^1]. A few decades later, Swiss scientist
Albrecht von Haller started to use the term epithelium/epithelia to
describe the fiber(s) of the body. The idea of fibers was an old
renaissance theory that the body is made of fibers, which was believed
to be a fundamental building block of living things.[^2] The
understanding then was that these fibers/tissues arranged in different
arrays gave rise to biological structures (maccord2012, zampieri2014).
Not far off as epithelial tissues are ubiquitous and cover most of the
organs inside out (contains more than 60% of the cells in a vertebrate's
body) (alberts2015). In twenty-first-century science, epithelial tissues
are understood as a type of animal tissue in which cells are packed into
sheets. The epithelial cell sheets have strong intercellular bonds that
form physical barriers to compartmentalize the organs and maintain
homeostasis. It plays a key role in developmental stages by supporting
growth and driving shape changes in the organs. It protects the organs
from external physical, chemical, and microbial onslaughts
(marchiando2010).

Epithelial cells are polarized, i.e., their apical side (faces the lumen
of the organ), which differs in shape and composition from the
basolateral side. Its polar organization is reflected in the vectorial
functions like creating and maintaining concentration gradients between
the separated compartments (marchiando2010). Typical examples of these
are transporting epithelia such as those of the renal tubule, absorptive
epithelia of the intestine, and secretory epithelial cells like
hepatocytes (alberts2015). In addition, polarized epithelia guide the
developmental process by determining the fate of cells leading to
symmetry-breaking events in the embryo (kim2018).

### Key components

Epithelial function primarily depends on the tissue's structure and its
microenvironment. It can be described in three parts: first, cell
structure; second, microenvironment; and lastly, cell-matrix
interactions.

#### Cell structure

In general, cell structure helps cells maintain their shape along with
providing mechanical support to perform vital functions like division
and migration (alberts2015). This structure is known as the cell
cytoskeleton. In particular, the Eukaryotic cell cytoskeleton is mainly
constructed out of filamentous proteins that hold the cell and its
cytoplasmic constituents. There are three major filaments, which differ
in size and protein content. Microtubules are the largest type of
filament of the protein tubulin, with a diameter of about 25 nm. Actin
filaments are the smallest type, with a diameter of only about 6 nm.
Finally, intermediate filaments are medium-sized, with a diameter of
about 10 nm (mofrad2009). Unlike actin filaments and microtubules,
intermediate filaments are constructed from several different subunit
proteins. All three types of filaments dynamically alter themselves in
reaction to signals from microenvironments and cell networks.

Mechanically, actin filaments are stiffer than microtubules in
extension, but they rupture at lower extension. The intermediate
filaments exhibit an intermediate extensional stiffness at lower
extensions and can sustain much larger extensions than the other two
types of filaments while exhibiting a nonlinear stiffening response
(wen2011). Differences in strength and stability come from the
properties of the individual subunits. The persistence length can vary
from 1µm for intermediate filaments to 1 mm for microtubules
(fletcher2010). Stiffest of all, actin filaments, have a persistence
length of a few microns.

The assembly and disassembly of these filaments are dictated by the
dynamics of their macromolecular components and accessory proteins.
Actin filaments in conjunction with myosin motors form the actomyosin
cortex which is critical for producing intra/intercellular forces. In
the case of epithelial layers, the actomyosin cortex and intercellular
junctions make cell-cell contacts stronger and provide integrity to the
tissue (braga2016). The perfect example of these tissue-level structures
can be seen in wound healing assays: cells surrounding the wound create
a ring of actin to close it (brugues2014). We will discuss the
actomyosin network more in detail in Chapter 3.

> Figure: Quilling of the human body and then showing apical-basal
> polarity of epithelial and monolayer including all the cytoskeleton
> and cell junctions and their mechanics

Multiple membrane molecules can mediate adhesion between cells. One of
these is cadherins, a critical component for epithelial cell cohesion
through the formation of adherens junctions. In these junctions,
cadherins are coupled to the cell cytoskeleton enabling force
transmission between cells. It is a key factor in the mechanical
regulation of division and tissue rearrangement during development and
homeostasis (godard2019, mertz2013). Desmosomes are another type of
intercellular junction. They are coupled with intermediate filaments,
and the resulting supracellular network confers mechanical resilience on
cell layers (hatzfeld2017, latorre2018). Tight junctions perform a
barrier function and enable the transport of ions across epithelial
layers to be actively regulated (marchiando2010). This plays an
important role in controlling fluid pressure in the tissues (chan2020).

#### Microenvironment

The extracellular matrix (ECM) is the cell environment or substrate to
which cells adhere; it is also known as the matrix, mesenchyme, or
cellular microenvironment. ECM serves many functions: it endows a tissue
with strength and thereby maintains its shape; it serves as a
biologically active scaffolding on which cells can migrate or adhere; it
helps to regulate the phenotype of the cells. It also provides an
aqueous environment for the diffusion of nutrients, ions, hormones, and
metabolites between the cell and the capillary network (alberts2015). On
top of that, it is subjected to mechanical forces such as blood flow in
endothelia, air flow in respiratory epithelia, or hydrostatic pressure
in the mammary gland and bladder (waters2012, walma2020). It is shown
that the ECM regulates cell shape, orientation, movement, and overall
function in response to biophysical forces (alberts2015).

ECM is a fibrous network of proteins; its three primary structural
constituents are collagen, elastin, and proteoglycans. Collagen is one
of the most abundant proteins in the body. Elastin is the most elastic
and chemically stable protein, and proteoglycans often sequester
significant water as well as growth factors, proteases, etc. Due to its
water content, the deformation of ECM can produce cracks in epithelial
layers. ECM acts as a poroelastic material, soaking up water upon
stretching (like a sponge) and releasing it under compression, causing a
hydraulic fracture effect (casares2015).

Moreover, the collagen network can remodel under the influence of cells
aiding in migration or mechanical forces (humphrey2014). Like most
cytoskeletal proteins, most extracellular components turnover. Some
continuously and some very slowly. For example, collagen in the
periodontal ligament appears to have a half-life of a few days, whereas
that in the vasculature may have a normal half-life of several months
(humphrey2013). In response to altered physical stimuli, disease, or
injury the rates of synthesis and degradation of collagen can increase
many folds to have a rapid response.

#### Cell-matrix interaction

Cells and ECM have a symbiotic relationship with each other through
various sensors on the cell surface. The biophysical cues are primarily
sensed using integrins and focal adhesion complexes in cell-substrate
adhesion (kechagia2019). Through these adhesions, cells can sense the
stimuli like matrix stiffness, ligand density, or chemotactic gradients
(fortunato2022). Recently, it has been shown that they could the cells
could even respond to the viscoelasticity of the matrix
(elosegui-artola2022). The cells also secrete ECM on their own or
remodel the substrate to promote growth/invasion of cancer or reorganize
the cytoskeleton altogether (malandrino2018). Due to the deeper ties of
focal adhesions to the nucleus and in turn transcriptional factors,
cell-matrix adhesions could affect the tissue behavior fundamentally
(venturini2020, lomakin2020). Precise control of cell-cell and
cell-substrate interactions enables cell sheets to transform themselves
into intricate curved forms (schamberger2022).

> Figure: ECM and focal adhesion.

### Role in disease and development

Epithelial integrity and homeostasis are of central importance to
survival, and mechanisms have evolved to ensure these processes are
maintained during growth and in response to damage. For example,
epithelial cells have one of the fastest turnover rates in the body. The
entire gut cell lining turns over in 5--7 days (barker2014). This
turnover implies constant cell division and death. The excessive rate of
division and death may give rise to tumors. It is known that 90% of
cancers emerge in simple epithelia (torras2018, eisenhoffer2013). Not
only this, but it could easily disrupt the barrier function, as no gaps
should emerge around dying or dividing cells.

If the fluid compartmentalization goes awry, it has profound
implications for epithelial and stromal homeostasis, fluid and/or
electrolyte balance, and the generation of inflammatory states. Several
bacterial toxins are known to target junctions and cause changes in the
tight junction protein ZO1, resulting in compromised barrier function
and pathologies such as diarrhea and colitis (fasano1991). The
compromised ZO1 barrier in cancer is essential to allowing metastatic
cells to break into and out of blood vessels. The leaky barrier also
allows a growing epithelial tumor to access luminal fluids as an
additional source of nutrients (mullin2005).

Moreover, epithelia participate in physiological events such as
epithelial--mesenchymal transformation (EMT), a developmental process
when epithelial cells gradually transform into mesenchymal-like cells by
losing their epithelial functionality. EMT plays a vital role in normal
biological functions like repair and differentiation; and abnormal
pathological activity like organ fibrosis and promoting carcinoma
progression (alberts2015). It endows cells with stem cell properties.
Thus, the mesenchymal state enables cell migration to distant organs and
allows their subsequent differentiation into multiple cell types during
development and the initiation of metastasis (thiery2009).

Epithelia undergo drastic changes in shape with deformation and
reorganization from the embryonic to the adult stage. Unsurprisingly,
any improper function would lead to damage and disorder. Defects in
morphogenesis results in congenital malformations, which are one of the
leading causes of infant mortality around the world (clarke2021).
Moreover, epithelial dysfunction is a precursor of diseases such as
chronic obstructive pulmonary disease, asthma, cystic fibrosis, or
pulmonary fibrosis (carlier2021).

### Forms of epithelia

Epithelial cells have different shapes and may be arranged in single or
multiple layers. They are usually classified according to two features:
the number of cell layers and the shape of the cells. Simple epithelia
are single-cell layers where all the cells contact the underlying basal
lamina and have a free surface on the apical side. The shape of the
cells can be flat (wider than high), cuboidal (as wide as high), or
columnar (higher than wide). However, stratified epithelium contains two
or more layers of cells.

> Figure: Different forms of epithelia and the range of shapes it takes

The classification in the nineteenth century was based on structure and
physiological characteristics. In parallel, embryologists expanded the
epithelial nomenclature with germ layer theory (maccord2012). During
early embryogenesis, three layers: endoderm, mesoderm, and ectoderm
emerge and maintain separate identities. Ectoderm creates the epithelia
lining the skin, mouth, and nervous system. Parts such as the digestive
tract, respiratory system, and liver are from the endoderm. While
mesoderm develops the endothelia which covers much of the circulatory
and lymphatic systems.

It is important to note that I will give many examples throughout the
thesis where the tissues are not exactly epithelia. They can be
aggregates of different cell types which are characteristically
epithelia-like. Our focus is simply packed cell monolayers, which can
form and organize themselves in an assortment of 3D shapes: ranging from
a simple sphere to complex branched tubules. In this thesis, we will
explore epithelial morphogenesis in a mechanical context.

## The mechanical basis of Morphogenesis {#the-mechanical-basis-of-morphogenesis-1}

### The complexity of the morphogenesis

During embryonic development, epithelia form transient structures, such
as the neural tube, somites, and precardiac epithelium, that serve as
progenitors for the development of more complex organs. Different
epithelia acquire diverse morphological forms and perform their specific
functions like branched lungs, looped gut, kidney tubules, thyroid
follicles, and sinusoids in the livers. Owing to its multifaceted
regulation and hierarchical organization, epithelial morphogenesis is a
complex phenomenon dependent on coordinated processes at
multi-spatial-temporal scales (trepat2018).

Some processes appear to be happening fast at the local level, like a
series of cells changing their shape by undergoing apical constrictions
to create a global change like the formation of a ventral furrow in a
Drosophila embryo (martin2009). However, at the same time, the chemical
signaling events activating this process are slow and at a global level.
Similar events are observed in *in vitro* systems. A cluster of
dissociated stem cells cultured in an appropriate medium assemble itself
into an organoid or a gastruloid (collinet2021). Just like the
drosophila embryo, this structure also undergoes local changes creating
global folds in response to global signals of culture conditions. It
gets even more complex when we consider the details of these processes.
For example, genes responding to the morphogen gradients, molecular
machinery implicated in apical constriction, or mechanical stresses
involved tissue scale deformations (schock2002, lecuit2011).

> Figure: Multi spatial and temporal scale events in the morphogenesis

Rudolf Virchow's third tenet of the cell theory stated '*omnis cellula e
cellula'* meaning 'all cells come from cells' (virchow1860)[^3]. All
tissues come from cells that contain essentially the same genetic
information. Nonetheless, every tissue exhibits a distinct architecture
and function. This raises many questions such as: what makes cells
different from each other? Is it all because of the genes? or
environmental factors? What drives the shape changes in tissue
morphogenesis? Since the advent of cell theory two centuries ago, the
field of developmental biology has answered a lot of these questions,
but it has also raised new issues and left open questions. The field,
until last decade, had been focused on the studies tracking and mapping
patterns of cell movements to patterns of a gene or protein expression
(gorfinkiel2021). These studies, while being greatly influential and
important to understand morphogenetic patterns; fall short of explaining
how cells and tissues are shaped physically. (veenvliet2021, odell1981).
Because physical understanding was only limited to the kinematic
description, which is the deformation of the tissue or motion of the
cells. As we know, the cell and tissues are actively driving these shape
changes and movements through the generation of mechanical forces
(lecuit2011). Thus, to have an integrated grasp of morphogenesis, we
must consider the role of forces and mechanics.

### On growth and form

Historically, the form for animate and inanimate objects has been tied
to function. As per the twentieth-century architecture principle of
"Form Follows Function"; where the organization of a structure should be
based on its intended function[^4]. In developmental biology, there are
many examples of this principle at work in self-assembling systems like
intestinal organoids, cancer spheroids, and gastruloids (gjorevski2016,
ishiguro2017, morizane2017). Each emerges out of a set of cells in an
appropriate environment changing and adapting itself in a specific form
to perform its biological function (vianello2019). However, exactly the
opposite design principle is at work in numerous in vitro experiments
with a controlled cellular environment; illustrating geometric
constraints drive biological function (xi2018). For instance, seeding
stem cells in bio-printed three-dimensional geometry of the
gastrointestinal tract produced functional tissues with physiological
characteristics of the intestine. The formation of a villus-like
structure can be controlled with curvature. (brassard2021).

> Figure: Form and function examples paralleling design to not design

Advanced microscopy techniques have enabled us to visualize each of the
developmental processes with clarity. We can monitor each cell and its
motion throughout the morphogenetic process: starting from a spherical
embryo to a complete organism (shah2019). Cells undergo shape changes
and large-scale flows to accomplish the task of morphogenesis (Reviewed
in labernadie2018, trepat2018). Mechanical forces are driving these
shape changes alongside the biochemical processes of gene patterning
(lecuit2011). Therefore, the dichotomy of form and function is
incomplete if we isolate it from the physical laws of mechanics.

> Figure: fish embryo development with velocities

More than a hundred years ago, D'Arcy Wentworth Thompson[^5] published
the classical text "On Growth and Form" (thompson1979), where he tries
to unravel the dialectics of morphogenesis by exploring the geometric
and physical constraints on living entities during development and
across evolution. Thompson compiled examples of how mathematics and
biology are related. Such as his theory of transformations, which shows
the differences between the forms of related species can be represented
geometrically. A famous example of this is transforming one type of fish
picture into another by deforming it[^6]. According to Thompson's
daughter, he used to entertain children by drawing pictures of dogs on
rubber sheets and stretching them to make poodles into dachshunds
(wolfram2022). This distortion of the shape is supposed to be
representative of significant alterations in various forces or rates of
growth throughout the developmental processes of different organisms.

Thompson's work is highly speculative. However, his broad idea was to
identify generalized principles behind the various biological forms and
patterns. He tried to illustrate this by comparing growth curves of
haddock, trees, or tadpoles; or by finding logarithmic spirals in
shells, horns, and leaf arrangements[^7]. Essentially, this book
emphasizes two points: first, all material forms of living
things---cells, tissues, and organs---must obey the laws of physics, and
second, quantitative measurements are necessary to unravel the physical
principles of biology.

> Figure: Transformation theory

Thompson's work has inspired many scientists from Alan Turing to Stephan
J. Gould; me and my advisers. Right as I began my Ph.D., the centenary
of the book\'s publication was being celebrated in the fields of
developmental biology and biophysics (heer2017, nat2017, natphys2017).
Even more so by the field of mechanobiology, an interdisciplinary field
that studies the role of biophysical forces in cell and tissue
functioning.

### Mechanobiology

> Figure: Tissues as a control system with different inputs and outputs;
> mechanotransduction

Each cell in epithelial tissue can be imagined as a mathematical system
which integrates several input types to result in an output behavior.
Such input cues may be mechanical, such as lung stretching, or chemical,
such as morphogen gradients in developing embryos, while outputs can be
cell deformation, migration, differentiation, or proliferation
(kumar2017). Some outputs could also feed back into the system as an
input, as in the case of cells remodeling the matrix (malandrino2018).
The sensing of the environment is mediated by mechanochemical switches
at the membrane, cell-cell junctions, or cell-matrix adhesions
(roca-cusachs2017). This sensing triggers the biochemical cascade
leading to a cellular response. This crosstalk between biochemistry and
mechanics is called 'Mechanotransduction'.

During morphogenesis, mechanotransduction occurs across the scales: from
a single cell to complex multicellular tissue. To parse out the role of
the different variables, experiments at different scales are needed. It
is seen that individual cells can sense their environment and respond by
altering their behavior through mechanical or biochemical processes.
However, the multicellular system can transmit forces and information at
a longer length scale (heer2017, lecuit2011). This enables them to
exhibit emergent characteristics such as collective migrations,
oscillations, rearrangements, and even turbulent flows (trepat2018).

A perfect example of tissue-environment interaction is durotaxis. The
epithelial cells can sense the matrix rigidity and migrate from low to
high stiffness. In vitro, cells in a monolayer collectively expand and
relocate to stiffer regions (sunyer2016). Similarly, durotaxis is
observed in vivo *Xenopus laevis* neural crest migration (shellard2021).
Not just the matrix affects the cells; the reverse is also true. The
durotactic gradient is generated by the migrating neural crest cells
themselves. In another example, Drosophila oogenesis, the disorganized
matrix is remodeled by cells into a polarized matrix, which aligns with
the actin bundles in the follicular epithelium through coordinated
rotation of the cells (haigo2011, cetera2014). These polarized fibers
can guide the directed motion of cells.

There is an interplay between an individual cell, its neighbors, and
exogenous stimuli. It is challenging to decouple various biophysical
aspects of the environment, such as forces, pressures, matrix stiffness,
spatial confinement, porosity, or viscoelasticity. Direct force
measurements in and out of tissues are even more difficult. To address
these challenges, scientists from various disciplines have attempted to
recreate experimental systems with precise control over the biochemical
and mechanical environments of the cells (xi2018). This has been made
possible by continuous technological advancement in fluorescent probes,
imaging, microfabrication, and force measurements (roca-cusachs2017). In
the following section, I highlight some relevant techniques and
experiments for mechanobiology.

#### Synthetic substrates

The simplest technique is to culture cells or tissues on 2D synthetic
substrates. Commonly, substrates like plastics (PET, PEGDA), hydrogels
(Polyacrylamide, collagen gels), and elastomers (soft PDMS) are used to
study mechanics because one can control rigidity, topography, and
mechanical forces (xi2018).

Polyacrylamide and soft PDMS gels have allowed researchers to
investigate mechanical interactions at cell-substrate adhesion. Just
seeding cells on different stiffness hydrogels reveals a drastic effect
on the actin cytoskeleton, shape, or on cell lineage specification
(yeung2005, engler2006). These substrates because of their known elastic
response are also used to measure forces through techniques like
traction force microscopy (TFM) (harris1980, gomez-gonzalez2020). TFM
studies showed that cells and tissues can exert higher forces on the
stiffer substrate because of remodeling of the cytoskeleton
(elosegui-artola2016). Higher matrix stiffness has been shown to induce
Yes-associated protein (YAP) translocation from the cytoplasm to the
nucleus, which could be considered as a sensor for mechanotransduction
(elosegui-artola2017). However, increasing ECM ligand density alone can
induce YAP nuclear translocation too without changing substrate
stiffness (stanton2019).

#### Geometric control

In 2D substrate spatial control on cells or tissues could be imposed by
using micropatterning adhesion proteins or microfabricated stencils. At
a cellular level, cells respond to the confinement by remodeling the
actin cytoskeleton and focal adhesion complexes according to the shape
(vignaud2012). Confined tissues undergo rearrangement at a larger scale
producing fascinating topological defects or oscillations (tlili2018,
balasubramaniam2021, guillamat2022). These experiments also uncover the
mechanism of force transmission throughout the tissues and cells during
collective cell migration, and epithelial growth regulation in two
dimensions (nelson2005, vedula2012, deforet2014).

The experiments with 2D embryonic stem cells show that differentiation
depends on the shape and size of the confinement. The tissue patterning
of a 3D gastruloid can be reproduced in 2D with a circular monolayer of
stem cells (warmflash2014). Also, the same cells confined in a triangle
could create high tension at the vertices and lead to Wnt signaling
(muncie2020). This signaling promotes differentiation to the mesoderm.

New photopatterning technologies aid in precisely controlling for
multiple proteins on the same substrate (guyon2021, prahl2022). This
enables us to establish a viable co-culture system for increased
complexity mimicking in vivo events.

As most of the epithelia in vivo are three-dimensional, the curvature of
epithelia is also a key factor to control. Using microfabrication
technologies like 3D printing and photolithography, we can create
substrates with topographical cues (schamberger2022). Epithelial
monolayers can sense curvature and respond by regulating cell migration,
orientation, cell/nucleus size, and shape (marin-llaurado2022,
schamberger2022). The epithelial monolayer on hemispheres of elastomers
would act as a fluid with increasing curvature (tang2022). However, at a
smaller scale with cells attached to a corrugated hydrogel, curvature
induces variations in lamins, chromatin condensation, and cell
proliferation rate (luciano2021). As mentioned before, bio-printing
three-dimensional geometry of tissue architecture could create
functional tissues (brassard2021, breau2022).

> Figure: Substrate and geometric control over the tissues

#### Mechanical control

Living systems do not just have spatial control, they also have
mechanical control through physical forces emerging out of growth,
deformation, and remodeling of ECM, and fluid pressure in closed
geometries*.* In our body, intestinal epithelia are stretched during
peristaltic movements in the gut and lung alveoli deform during
breathing. Not just tension, compression is known to guide several
morphogenetic events involving tissue bending and folding, such as the
formation of the optic cup, gut villi, and cortical convolutions in the
brain (okuda2018, shyer2013, tallinen2016). To understand tissue
behavior under external perturbation, cells and tissues are probed at
the molecular and subcellular scales using, atomic force microscopy,
magnetic beads, optical tweezers, and micropipettes (bao2003). At a
larger scale, various kinds of stretching devices, tissue rheometers and
force plates can be used (xi2018).

These tools allow for probing biological materials with controlled force
or displacement, which is also useful in characterizing their
rheological properties. These experiments reveal that cells have a
complex viscoelastic behavior at different regimes of deformation
involving different parts of the cytoskeleton (mofrad2009). Whereas on
stretching the tissue, the cells within the tissue can reorganize or
stretch depending on the timescale of the stretch (guillot2013). Also,
with the help of rheological experiments, the role of signaling pathways
in terms of transcription factors like YAP in mechanosensing is
elucidated (wagh2021).

> Figure: Mechanical control over the tissues

#### Microfluidic chips

In the purview of cell mechanics, the microfluidic system---cells on a
chip--- has been proven as an outstanding tool for mimicking in vivo
conditions and controlling biophysical cues; enabling us to study cell
behavior (ingber2018). It is a practical way for applying stretch/shear
forces or creating a controlled microenvironment. Organ-level cues, like
surface tension at an air-liquid interface in the case of the lungs, as
well as both fluid flow through the vasculature and cyclic mechanical
stretch of the tissue-tissue interface due to breathing motions, can be
recreated (huh2010).

In developmental biology, culturing iPSC-derived motoneurons and brain
microvascular endothelial cells together on a similar chip produced the
neuromuscular unit with in vivo-like maturation of spinal cord neural
tissue (sances2018). This opens new avenues to develop the current view
of self-organization and embryo functions with controlled physical
conditions (samal2019).

> Figure: Microfluidics and cell aggregates

#### Matrix independent

As mentioned earlier, the tissue-matrix interaction is playing a
critical role in sensing and transmitting forces rapidly (tambe2011,
sunyer2016, serra-picamal2012). However, in early embryonic epithelia
where little or no ECM is present, stresses generated by actomyosin
contraction of the cells in one tissue are transmitted over long ranges
via intercellular adhesions to other tissues. Thus, the system of
studying just simple free-standing epithelial monolayer is very
appealing in terms of characterizing mechanical response to stretch at
different time scales. There are only two techniques available for this.
One, Harris and colleagues created a suspended monolayer by culturing a
cell monolayer on a collagen matrix on two rods; later matrix was
removed using enzymatic digestion (harris2012). Second, epithelial
domes, where MDCK cells pump ions to form fluid-filled blisters
(lever1979). Recently, the control over the curvature, shape, and size
of the domes is enhanced even more by my colleagues, Ernest Latorre and
Ariadna Marin-Llaurado (latorre2018, marin-llaurado2022, Details on this
system in the next chapter). These experiments showed that elasticity
measurements of the monolayer were two orders of magnitude larger than
that of individual cellular parts, and the monolayer could sustain more
than 200% strain before the rupture of cell-cell junctions. The cell
cytoskeleton particularly the actomyosin network and cadherin junctions
actively remodel during stretching, also the keratin network reinforces
the monolayer integrity at higher strains (latorre2018, duque2023). At
sustained stretching, the tissue undergoes significant realignment and
rearrangement via division (wyatt2015). The experiments on tissue devoid
of the matrix also revealed epithelial actions such as superelasticity
and buckling (latorre2018, wyatt2020).

#### Cell aggregates

Many of these in vitro experiments with 2D or 2.5D systems have improved
our understanding of cell mechanics in morphogenesis. We could measure
deformations and forces along with controlling the environmental
conditions which are inaccessible in vivo systems. However, to elucidate
further the mechanics must be probed at systems closer to in vivo
systems.

Cell aggregates have become viable in vitro systems where mechanics
could be probed. The engineering techniques for synthetic matrix and
mechanical measurement tools could be used for this system too. Cell
clusters are shown to respond to the matrix as planar tissues but with
increased complexity. They could sense matrix stiffness, confinement,
and ECM concentration along with undergoing 3D shape transformations.
Our lab has shown that cell aggregates perform durotaxis and are
actively wet or de-wet dependent on stiffness (perez-gonzalez2019,
pallares2022). The cell aggregates in suspension resemble a viscous
droplet. This behavior is exploited to measure rheological properties.
Aggregates squeezed between plates, probed with AFM or micropipette
inform us about its mechanics (xi2018). Even coalescing two aggregates
could allow for measuring the viscoelastic properties (oriola2022).

Cell aggregates can be embedded into a hydrogel. The most common types
of hydrogels are PEG, polyacrylamide, collagen, or Matrigel. Naturally
extracted hydrogels like Matrigel provide a similar architecture to
native ECM. Most of the epithelia are polarized, so when embedded into a
hydrogel they tend to form a spherical structure with a hollow lumen.
However, under the action of hepatocyte growth factor, the branching
morphogenesis is induced (bryant2008).

The cell-driven self-assembly in organoids leads to the formation of
tissue with features mimicking an organ. However, the reproducibility of
shape and composition is often tricky (nelson2008, hofer2021). 3D
hydrogel system has proven greatly useful with epithelial organoids. The
control over ligand presentation, crosslinking, and degradability of
synthetic hydrogels allows for control of cell fate (gjorevski2016,
gjorevski2022).

3D gel-based culture systems are also developed with spatiotemporal
control on the mechanical properties that correspond to the in vivo-like
functional structures (torras2018). Interestingly, some recent
publications show tissue transformation of planar tissue to complex
organ-resembling tissue without finer control of the environment.
Intestinal epithelium mechanically compartmentalizes itself, and 2D stem
cells transform into a 3D neural tube (perez-gonzalez2021,
karzbrun2021).

#### In vivo systems

In developing embryos, embryonic and extraembryonic fluids generate
forces: frictional and tensional stresses when flowing, or hydrostatic
pressures when in confined spaces (vianello2019, chan2020). Measuring
forces poses a great challenge in this system. Micropipette has been one
of the prominent methods to manipulate these tissues.

Micropipette experiments, where the needle is inserted into the embryo
to control pressure, revealed that internal hydrostatic pressure
determines the embryonic size and directs the allocation of cell fates
(chan2019). As a fluid-filled structure, imagine a balloon, the
hydrostatic pressure inside relates to tension in the surfaces. Any
changes in luminal volumes are sensed by cells through the increased
cortical tension, which in turn induces changes in cell shape and
cytoskeletal organization (chan2019, choudhury2022). Micropipette
aspiration is an effective tool in measuring the surface tension of
individual cells or the whole blastomeres (dumortier2019). These
experiments explain the role of the actin cortex in governing the
contractility of preimplantation embryos (ozguc2022, firmin2022).

Measuring forces in the interior of the embryos could be solved by
inserting a deformable probe into the tissue such as hydrogel, oil, or
magnetic droplets (dolega2017, campas2014, serwane2017). The shape
changes allow for measurement of local forces as well as osmotic
pressures inside (mongera2023).

Besides embryos, explant systems are utilized to understand the
organogenesis of the brain, gut, or lungs. Lung explant research has
been a fantastic way to understand different aspects of shape formation.
Lungs start as an evagination of a foregut tube which later buds and
bifurcates to form a branched organ. This occurs under different stimuli
of pressure and growth factors. The explant system allows direct control
of the chemical and mechanical environment right at a specific stage of
development. Work with mouse airway epithelium shows pressure and the
matrix stiffness affect the number of branches (palmer2021, varner2015,
nelson2017).

There are other tools like optical tweezers, laser ablation, or
optogenetic excitations used at different levels for probing the
mechanics of development (lecuit2011, gomez-gonzalez2020). Yet,
independent control over different discerning factors is incredibly hard
and the force measurement remains indirect.

To sum up, epithelia are actively responding to various biophysical
forces and constantly undergoing remodeling at different lengths and
timescales. There are technologies available to manipulate from single
cells to embryos with controlled forces and deformation. Epithelial
tissue may be thought of as active material based on how it behaves. In
the next chapter, we delve into how these tissues are active and what
molecular machinery drives them.

## Active tissue mechanics {#active-tissue-mechanics-1}

### Force generation via Actin cytoskeleton

Most of the morphogenetic processes involve cells changing shapes to
sculpt a specific form. In the nineteenth century, embryologists,
observing the mechanical processes of individual cells in a tissue,
thought that there must be an external vital force guiding the
morphogenesis (thompson1979). Experiments of Wilhelm His and Wilhelm
Roux and later ideas of D'Arcy Thompson made it clear that the physical
forces guide the shape change of the cells[^8] (clarke2021). Now we
know, what was unknowable in the 19^th^ century, the machinery for
generating the forces is the actin cytoskeleton. In a cell just beneath
the plasma membrane, the actomyosin cortex forms a mesh containing actin
filaments along with myosin motors (alberts2015). This mesh is organized
into various higher-order arrays capable of dynamic remodeling. We can
understand the actomyosin cortex step by step: from its basic
organization of single actin filament to higher-order supracellular
actomyosin cables.

#### Actin filaments

Actin filaments are helical polymers of actin proteins (G-actin).
Asymmetrical actin proteins connect to each other in the same direction
giving the filament structurally two different ends and polarity. These
two ends are referred are barbed or pointed ends because of their
appearance in electron micrographs. They are dynamically assembling and
disassembling. Because the distinct ends have different kinetics rates,
the actin filament grows in the direction of the barbed end. As there is
a pool of monomers in the cell and nucleotide hydrolysis process, a
filament with both sides exposed will maintain its length but the
subunits would be in constant flux. This event is known as treadmilling.
Although, if one end is capped the filament will continue to grow and
apply pushing force in the outward direction.

#### Actin networks

Actin filaments can also form branched networks. These are assembled by
creating nucleation sites on a filament with proteins that contain
actin-binding motifs. Actin nucleation can be catalyzed by two factors:
the ARP 2/3 complex or the formins. ARP 2/3 complex creates a pointed
end in the middle of a filament leading to the formation of a new branch
from that site. These branches turn into a tree-like web that can apply
pushing forces enough to push a part of the cell membrane. The formins
along with profilin enhance the growth of the filaments. Profilin in
this process is used as a staging area for the rapid addition of
monomers to the filaments. These structures could be dendritic actin
networks that enable membrane protrusion at lamellipodia or spike-like
projections of the plasma membrane that allow a cell to explore its
environment. The pushing forces generated at a molecular level are
around 1 piconewton order.

> Figure: Actin filament to bundles

#### Actomyosin bundles

Another way actin filament organizes is by forming tight or loose
bundles with help of crosslinking proteins. With fimbrins, multiple
actin filaments can arrange themselves in parallel. As it is a small
monomer, forms closely packed bundles that exclude myosin for connecting
to the filaments. On contrary, α-actinin crosslinks actin filaments with
opposite polarity into a loose bundle. This allows myosin to bind and
create contractile bundles. Myosin II oligomerizes into a bipolar short
filament that can connect multiple actin filaments and move across the
filaments creating a pulling effect.

The loose bundle forms the gel-like network for the cell cortex. There
are a number of other actin crosslinking proteins that can lead to a
different structure. Filamin creates a loose and viscous gel needed for
migration. Whereas spectrin creates a strong and flexible weblike
network of short actin filaments allowing cells to reversibly deform.
The actomyosin bundles in the cortex could generate two orders of
magnitude more force than a single filament (clarke2021).

#### Actin structures organized at a larger scale

During epithelial morphogenesis, cells change shape individually by
altering the contractility or actin turnover to develop the curvature of
the tissue. As seen earlier the epithelial cells have apicobasal
polarity. This polarity creates a non-homogeneous distribution of actin
cytoskeleton, which affects the cell shape and tissue architecture.

Geometrically, the cells of columnar or wedge-like can only be organized
in specific ways in a monolayer (gomez-galvez2021). Columnar cells
together will make up a flat tissue. Wedged cells with a narrow top will
create convex curvature. Another way is concave curvature with a narrow
bottom. By monitoring the actin cytoskeleton, we can discern the
specific mechanism of the tissue shape. Apical constriction with
concentrated actin cortex on the apical surface is implicated in
multiple convexly curved tissues like invagination of the intestinal
crypt, drosophila mesoderm, and vertebrate lens placode
(perez-gonzalez2021, lecuit2011, houssin2020). Opposite curvature is
seen after basal constriction in an optic cup and mid-hind brain fold of
zebrafish (sidhaye2017, gutzman2018).

However, similar convex curvature in the tissue can be produced through
basal expansion as in the case of the drosophila wing disc. Some parts
of the wing disc locally relax the basal side without affecting the
apical side causing basal expansion (sui2018). Besides apical and basal
surfaces, lateral surfaces can also contract or expand with myosin II
activity. This could produce tissue folding in the wing and leg disc of
drosophila (sui2018, monier2015); or produce cell-cell rearrangements by
changing junction lengths during its germ band extension (yu2016,
collinet2015).

Not only the coordinated actin reorganization in cells but also
tissue-wide supracellular actin structures can emerge. Junctional
actomyosin organizes to form bundles connected across multiple cells to
perform vital tasks such as wound healing and morphogenesis
(brugues2014, clarke2021). These supracellular networks could exert
forces at the embryo scale seen in cases such as drosophila's dorsal
closure and parasegment boundary formation, or zebrafishes epiboly
(ducuing2016, calzolari2014). These supracellular networks also change
the material properties of the specific regions in the embryo making it
easier for them to deform to form folds or invaginations. During
Drosophila gastrulation, tissue level actin cortex is altered in
direction of the anterior-posterior axis giving it more bending strength
in that direction. This in turn aids in the internalization of the
mesoderm by supporting folding in a perpendicular direction
(yevick2019). Interestingly, in even larger systems such as Hydra,
vertebrate smooth muscle, and heart highly organized actin bundles are
often found (maroudas-sacks2021, palmer2021, cetera2014, helm2005). They
assist in generating mechanical force patterns to create global
coordinated tissue movement.

#### Timescales of the actin cytoskeleton

Morphogenesis occurs at different timescales, and the cell cytoskeleton
has to undergo shape changes with those timescales. The rheological and
mechanobiological experiments have provided us with insights into their
response. Cells respond to the forces and deformations according to
their magnitudes and rates (reviewed in wyatt2016).

Fast deformations (milliseconds to seconds) are typically associated
with elastic behavior as there is not enough time for the actin cortex
to respond or remodel. The cytoskeleton can store the elastic energy and
give it back. At this scale, there is also a flow of cytosol through
cortical mesh leading to poroelastic behavior.

However, the forces or deformations applied at longer timescales
(seconds to minutes) reveal viscoelastic behavior. The cortex could flow
and is not able to store energy completely. The turnover of actin
filaments and various crosslinkers allows the actin cytoskeleton to
remodel effectively in reaction to mechanical perturbations. Actin
filaments and myosins turn over in tens of seconds, while other
crosslinkers like actinin turn over in a few seconds. However, the
myosin mini filaments could take longer to remodel in the order of
hundreds of seconds.

At even longer timescales (minutes to hours) the cells or tissues could
respond through oriented divisions or rearrangements. It can adapt to
persistent forces such as gravity or surface tension. Also, it could
cause tissues to resemble viscous fluid and morph into a sphere as a
blastocyst. Although tissues are seldom without an extracellular matrix,
hours of interaction with surroundings lead tissues to adjust their
constitutive tension following biophysical and biochemical forces.

#### Controlling cortical tension

However, the magnitude of contractile or extensile forces applied by
cells depends greatly on the tissue and its environment. The signaling
of crosslinkers and nucleators of actin bundles is regulated by external
biochemical and biomechanical stimuli (reviewed in kelkar2020). As the
actin filaments, the actomyosin bundles are also dynamic. They
constantly undergo contraction, polymerization, and depolymerization, in
the normal state, while producing a homeostatic level of cortical
tension. As many moving parts are involved in the actin network,
cortical tension of cells can be easily controlled with pharmacological
treatments targeting specific molecules (cartagena-rivera2016).

The contractility can be reduced with Latrunculin which binds to the
actin monomers leading to the depolymerization of the network.
Inhibiting myosin activity with Blebbistatin results in a decrease of
cortical tension too. Blebbistatin hinders myosin II ATPase activity.
While Calyculin-A increases contractility by enhancing the rate of
Myosin II phosphorylation. Cortical tension could also be boosted by
sequestering ARP 2/3 monomers with CK666. There are other factors like
Rho-GTPases or calcium levels further away in the signaling pathway
which could affect the stability of the network (valon2017).

Optogenetic tools give finer and more localized control over
contractility. The tools based on the regulation of RhoA can locally
control cell protrusion, tissue tension, and traction (valon2017). A
recently developed tool controlling Shroom3 gives finer control over
apical constriction. It can be used to recreate tissue folding
(martinez-ara2022).

### Modeling active tissue dynamics

We are increasingly able to understand the tissue dynamics and molecular
pathways responsible for morphogenesis. However, it has become very
important to interpret biological experiments with a theoretical model.
The model and its hypothesis could inspire us to come up with intriguing
predictions or launch new trials to validate them.

There are mathematical models describing physics and biology at multiple
scales. There are hyperelastic continuum material models at larger
tissue scales, for describing the behavior of the cardiovascular system.
There are agent-based models for relatively smaller scales explaining
epithelial tissue behavior in terms of cell sorting or reorganization. I
will introduce the reader to pertinent modeling approaches in a brief
manner.

#### Vertex model

D\'Arcy Thompson, in the chapter on "The forms of tissues", makes a
super intuitive argument regarding the role of surface tension or
capillarity to organize cells together in a tissue. This was visible to
him ubiquitously in nature from two connected cells to the organization
of cells in the dragonfly wing. These resemble associations of soap
bubbles or foams.

Monolayered epithelial tissue has a polygonal cellular pattern on its
surface. This enables one to describe/track cell motion and shape change
easily in terms of vertices and edges. Vertex models have been valuable
to understand the complex interaction between cellular shape, the forces
generated inside epithelial cells, and mechanical constraints externally
imposed on the tissue (Reviewed in alt2017). Models could be 2D or 3D
depending on the system being modeled, but cells are consistently
defined as each one has an apical and basal surface and lateral
interfaces between neighbors. More complexities have been added to
describe specific systems like intercalations in 3D epithelia using
geometric shape as Scutoid.

To determine the motion of the vertex, mechanics must be specified. It
is often done using the virtual work function (W). There are two
components: internal and external.

\$\$ \\delta W = \\delta W_i + \\delta W_e \$\$

The changes in internal virtual work, \$\\delta W_i\$, can result from
changes in the cell volumes, in the areas of surfaces, or in the lengths
of bonds. By defining the cell pressure, the surface tension, and the
line tensions, the differential of the internal virtual work for vertex
movements can be written.

\$\$ \\delta W_i =

\\Sigma\_{cell \\alpha} -P\^\\alpha \\delta V\^\\alpha

\+ \\Sigma\_{surface k}T\^k \\delta A\^k

\+ \\Sigma\_{edge \\lambda} \\Lambda\^\\lambda \\delta l\^\\lambda

\- \\Sigma\_{vertex \\nu}f_i\^\\nu \\delta x\^\\nu \$\$

Similarly, the external virtual work, \$\\delta W_e\$, can be written
according to the external forces that come from external mechanical
forces applied to the tissue through the matrix, or fluid pressure
acting on apical or basal cell surfaces.

The state of the monolayer is estimated by minimizing the virtual work
function. Here, molecular complexities are incorporated in the
definition of surface tension and line tensions. Particularly for the
epithelial layers, the actin cortex plays a huge role in determining
tensions along the edges. In 2D models, vertex model simulations show
the role of interfacial tensions in guiding cell orientation, collective
migrations, and tissue rearrangement through cell divisions.

Whereas the 3D or 2.5D models captured the physics of different
morphogenetic processes from appendage formation on drosophila eggshell
to mechanical compartmentalization of intestinal epithelia. Also, these
simple models provided unique insights about cell packing and the
jamming/unjamming transitions. In some cases, there are phase
transitions from solid to fluid states emerging due to localized
proliferation and oriented divisions. The epithelial tissue behaves as
an active material with viscoelastic properties.

#### Continuum models

Viscoelastic properties of the tissues are captured in the vertex
models. However, in the instances where the focus is on larger-scale
deformations or flows, we can model them as a continuous material. Here,
I would discuss two tactics for thinking about these models. One is
related to the material properties of the tissues. It involves probing
the tissue behavior in terms of rheological properties. The second is
about shape transformations. How a continuous sheet of cells can fold up
during development. It can be thought of as an active surface and using
this model the physics of single cell to embryo can be captured at once.

The soft tissues respect the basic postulates of mechanics, and basic
concepts such as stress, strain, and entropic elasticity. Hence, much of
the continuum models focus on the formulation of reliable constitutive
relations and then on the solution of initial-boundary-value problems.
Constitutive relations describe the response of a material to applied
loads, which depends on the internal constitution of the material.

However, the determination of constitutive relations is tricky for
materials such as epithelial monolayers. These tissues are much more
complicated materials than those simple metals or passive polymers.
However, the complex material behavior can be understood by
characterizing mechanical response using standard material testing
techniques. Typically, it is done by probing the tissue mechanically in
a biologically relevant manner. For example, biaxial or uniaxial
stretching of the tissues to recapitulate the in vivo tissue behavior.
These experiments reveal the viscoelastic nature of the material.

##### Viscoelasticity

Solids like rubber are considered elastic where the material can
reversibly deform under the application of force. On contrary, the
fluids are viscous. They flow on the application of force. The
viscoelastic material behavior is a combination of solid-like and
fluid-like properties. The simple models can represent the rheology
through a combination of the elastic parts as springs and viscous parts
as dashpots. The elastic response is non-dissipative as compared to the
viscous one.

\$\$ \\sigma = E\\epsilion \$\$

\$\$ \\sigma = \\eta \\frac{d\\gamma}{dt} \$\$

The quasi-static stretching or compressing can reveal the stiffness or
Poisson's ratio. However, dynamic properties are understood through
frequency sweep, creep, or stress relaxation experiments. Rheological
experimentation has been greatly useful in understanding the mechanical
response of different biological materials: from reconstituted
cytoskeletal proteins to large multicellular aggregates.

The rheological properties often correlate with their physiological
state and are crucial for their specific functions (Park, J.-A. et
al. 2015; Vedula, S. R. K. et al. 2015, Vedula, S. R. K. et al. 2014).
For example, Heart failure is often due to the loss of contractility of
heart muscle cells; as is observed in remodeling under mechanical
stretch (Fung YC, 1990). So, one must test rheological properties along
with different microenvironments. The mechanical information includes
deformation, rates of deformation or velocity fields, traction forces
exerted by cells on the substrate, and intercellular mechanical stress.
Coupling these parameters with information on cellular architecture,
obtained by imaging, can provide a mechanistic understanding of tissue
rheology (roca-cusachs2017). These kinds of experiments reveal complex
mechanisms of strain stiffening and viscoelastic behavior at different
regimes of deformation involving different parts of the cytoskeleton.

##### Hyperelasticity

However, in certain cases like modeling cardiovascular mechanics or the
growth of organs, we can rely on hyperelasticity or composite material
framework. The basic kinematics assumes a mapping, \$ x = \\chi (X,
t)\$, deformation from reference to deformed configuration. The
deformation gradient and Green's strain tensor are defined.

\$\$ F = \\nabla_X (\\chi(X, t))); E = (F\^T F -- 1)/2 \$\$

The elastic and growth can be delineated in the deformation gradient
through decomposition.

\$\$ F = F_e F_g \$\$

Here, in the theoretical framework of finite elasticity, one can assume
a strain energy function relates to stress. The stress-strain data
extracted from the experiment allows for predicting the form of the
strain energy function.

\$\$ S = \\frac{\\delta W}{\\delta E}

In the case of the bladder, heart tissue, skin, and arteries,
hyperelastic form has been useful in capturing the material response.
This kind of formulation is also flexible in adding extra physical
constraints as anisotropy of the tissue microstructure or its
incompressibility. Borrowing from composite materials, transversely
isotropic material models have been instrumental in understanding
mechanisms of myocardium infarction and various aneurysms. Slight
modification to these constitutive relations could capture material
response, such as explaining strain stiffening, or inhomogeneity in the
material like accounting for collagen content and crosslinking in the
tissue.

These models are also used in understanding growth and remodeling by
using the theory of kinematical growth. It has pointed out the existence
of residual stresses in growing tissue to make compatible elastic and
inelastic growth-induced deformations, which in turn remodel the tissue
properties modifying the material into a spatially inhomogeneous and
anisotropic one. This process is crucial in solid tumor growth
mechanobiology, the residual stresses directly influencing tumor
aggressiveness, nutrients walkway, necrosis, and angiogenesis.

##### Nematic active mechanics

At the cellular scale, we know that the mechanical properties of the
tissue are controlled by the biopolymeric cytoskeleton. Filaments and
their cross-linkers (molecular motors) continuously transduce energy
(ATP to ADP) to contract or extend the network. This system can be
considered a physical gel because of its cross-linked actin filament
network. But phenomena like treadmilling, active
polymerization-depolymerization of filaments, and mobility of molecular
motors like myosin makes the tissue system an active gel. Also, note
that the cellular system lacks time reversal symmetry because it is
constantly transducing energy.

Moreover, these filaments are polar, as constituents can acquire
orientational order. Thus, one can model tissues as active gels; are
used to model active systems like flocks for birds and schools of fish
using hydrodynamics of active matter. Active matter systems are a
subclass of continuum models used to describe the dynamics of packed
active particles; based on liquid crystal theories of soft condensed
matter. Like liquid crystals cells too have orientation and the ability
to move past each other. In this framework, one characterizes the
orientation of filaments in the cytoskeleton or elongation of cells in
the tissue by nematic order parameter matrix.

\$\$ Q = 3S(nn -- I/3)/2 S = \[cos2\\theta\] \$\$

\$\$ \\sigma_active = \\Zeta Q \$\$

This formulation aids in defining active forces generated by the
network. The stress is divided into two parts: active and passive. Where
passive stress will be arising from the mesoscopic viscoelasticity of
the material and the bending, splaying, and twisting of the aligned
agents. Active stresses are obtained using a combination of zeta, the
strength of activity, and the nematic order matrix. Zeta's sign
determines the nature of the force dipole. If negative, the system
contracts; if positive, the system expands along the nematic axis. For
example, actomyosin systems are contractile. Active stress is very
crucial for the motion of the system. Even in low Reynold's number
systems, the motion could get chaotic. In a dense bacterial system of
Bacillus subtilis, jet flows and turbulent flow patterns were observed.
Also, independent vortices have been observed in the expanding
monolayers. Nematic equations have captured physics very well in 2D
confined systems or expanding systems.

##### Active surfaces of the actin cytoskeleton

For 3D, active surfaces are used. The actomyosin cortex near cell
membrane or epithelium in the embryo is like a thin sheet of matter,
which drives shape changes at the cellular or tissue level by causing
deformation due to the generation of internal forces and torques. These
three-dimensional structures resemble a curved active two-dimensional
surface. The framework developed for active matter can be used by
applying mathematical tools from differential geometry. The curved
surface is defined in generalized coordinates \$X\$. The metric tensor
\$g\$ and curvature tensor \$C\$ are used to describe the kinematics.
And forces and torques are defined as, where \$dl\$ is the length of the
line element with tangential unit vector \$v\$ normal to the line, and
\$t\$ and \$m\$ are tension and moment respectively. In this framework,
the mirror and rotation symmetries of the surface elements are also
considered.

Figure: active surfaces from Salbreux and Julicher 2017

Salbreux and Julicher show that flat active membranes with up-down
asymmetry have stability dependent on active tension and active
tension-curvature coupling term. This tension-curvature dependency can
be seen in the pancreas of mice the morphology of epithelial tumors is
determined by the interplay of cytoskeletal changes in transformed cells
and the existing tubular geometry (messal2019). Consistent with theory
predictions: small pancreatic ducts produced exophytic growth, whereas
large ducts deformed endophytically. Another example shows that curls of
high curvature form spontaneously at the free edge of suspended
epithelial monolayers (fouchard2020). It is pointed out that the curling
originates from an enrichment of myosin in the basal domain that
generates an active spontaneous curvature. It was shown that the extent
of curling is controlled by the interplay between internal stresses in
the monolayer.

Overall, the molecular level behind the epithelial morphogenesis, actin
cytoskeleton, is well understood. There are modeling approaches to
elucidate the functioning at different scales from filaments to whole
tissues. The phenomenological experiments provide insights into the
constitutive relations of cytoskeletal components and tissues in
specific conditions. Vertex and continuum models capture the physics of
morphogenesis at the tissue scale. The theoretical and experimental
framework is lacking to bridge the gap between molecular dynamics and
tissue scale deformations. The vertex models and active surface
mechanics could be combined to give finer control over the individual
cell surface. In the next chapter, we will discuss bottom-up
morphogenesis.

## Bottom-up morphogenesis {#bottom-up-morphogenesis-1}

### Learning by building

It is very clear that the mechanics and biology of the epithelial
tissues are complicated; intertwined by mechano-chemical signaling; and
multiscale in their behavior. The lens of active material has been very
helpful in providing information on the role of molecular elements in
performing the biological function. These studies have also led to
examining emergent behaviors which would be impossible in vivo. The
mechanistic understanding has been enhanced with newer mathematical
tools and advanced microscopy; enabling us to measure forces involved in
the tissues.

Engineering in biological systems has pushed our limits in understanding
physiological response, morphogenesis, and pathologies. However,
engineers are not just attracted to this subject for its application in
health and disease, but for its potential to inspire the construction of
new materials or engineering systems. In many instances, where new
materials have been fabricated inspired by biological matter. Also, an
improved understanding of biological systems has provided new methods
for creating organically optimized systems.

Biomimetics is a field where nature continuously inspires human
innovation: from hydrophobic surfaces to supersonic passenger planes!
Here, epithelial tissue has displayed incredible capabilities such as
self-assembly, self-healing, and self-replicating. This makes it a very
interesting material for engineers as its study provides new ideas in
the strength, adaptability, flexibility, and functional aspects of the
material.

However, experimentation with systems like organoids or embryos can only
provide insights into the autonomously formed structures. This
information is useful, but the topological transitions of these
structures are not fully understood. An interesting proposal is to learn
by actively doing morphogenesis. The critical pedagogist, Paolo Freire,
had the philosophy of learning through an active practice called
'praxis/learn by doing.' We can extend it to learn by building
epithelial structures.

A lot of synthetic biology is based on the idea of learning about
biology by recreating it from scratch. Also, it gives an enhanced
understanding of which components are indispensable for the desired
function. Researchers are working on different scales to recreate life:
starting from synthetic proteins to a cell. However, I would focus on
the mesoscale (\~10-10^4^µm) structures of epithelia.

From a physics perspective, at this scale of multicellular forms, we
will be in a perfect position to recreate emergent properties which play
a key role in many systems. This reminds me of the example of cars and
traffic (good2018[^9]). We can understand the function and behavior of
each of the car components and drivers, but this information would not
allow us the study the behavior of the traffic jams. One could even
think about the traffic flows as a living and breathing organism.
Assuming to solve the problem at the scale of traffic, we could learn
much more about the transportation issue by just building the network.

What is even more interesting is that while building a structure we
could encounter instabilities, emergent phenomena, or see the system
self-organize around an alternative path. A perfect example of this is a
desired path page on the internet, where people tend to carve
energy-efficient paths around the instructed paths.

In this work, we have tried to create a system to engineer an epithelial
structure with a controlled microenvironment. At the same time, it is
sensitive to undergo self-organization and mechanical instabilities. In
the following sections, I will explain how we can make these structures
from the scratch, and relevant mechanical instabilities.

### How to build epithelial structures?

Before starting to build the epithelial structure, one must ask
questions related to form and function. Despite the diversity in forms
and functions of epithelia, there are elementary shapes emerge
everywhere through the coordination of physical force and biochemical
signaling. Shapes such as spherical blastocysts, ellipsoidal embryos, or
cylindrical vessels.

To construct any of these structures, well-established cell lines are
used. Researchers choose the cells according to the relevant systems.
For example, epithelial cells for recapitulating intestinal crypts,
endothelial cells for vasculature, or fibroblasts for cancer stroma.
However, the building of the synthetic structure is done through
different techniques from controlling geometry to engineering localized
folding (many of these are discussed earlier in chapter 2 mechanobiology
section).

#### Controlling geometry and physical forces

Scaffolding is the most intuitive way to create these structures from an
engineering point of view. A scaffold can be created using 3D printing
or various microfabrication techniques. Then cells are seeded to create
the desired shape. In this approach, the cells are provided with a
well-controlled microenvironment in terms of geometry, stiffness,
adhesion proteins, and appropriate cell culture media. The structures
created through this method could be used to study tissue behavior in
response to the forces and curvature.

Dessalles and colleagues prepared a hydrogel with a cylindrical hole,
which they used for culturing the endothelial cells to form a
micro-vessel (dessalles2021). The hydrogel with cells inside is housed
in a microfluidic device which can control the pressure and the flow in
the vessel. They were able to uncover the role of the poroelastic
properties of hydrogel in regulating the dynamics of the vessel.

The scaffolds could even dynamically change their shape. As in the case
of cell monolayer on a flexible membrane allows to change in the
curvature of the tissue (blonski2021), or the cell-laden hydrogel
through a combination of stretching and un-stretching creates
distinctive patterns and folds (chan2018). In some fascinating studies,
researchers used 4D bioprinting, where 3D printed object transforms with
time (arif2022). A flat hydrogel sheet with endothelial cells on
photo-crosslinking can be transformed into a tube (zhang2020).

Some have used the contractility of fibroblasts and hepatoma cells to
fold 2D structures into 3D (he2018). Here, microplates are created in
the origami folding pattern, and on seeding the cells apply forces to
construct a 3D shape. While others have used the ability of cells to
self-organize only by dictating the geometry and hope that the cells
differentiate and localize themselves into specific regions. This
externally imposed geometric constraint improves the efficiency of
organoid-like systems (gjorevski2016). For intestinal organoids, even
controlling the stiffness of the matrix in certain areas leads to growth
and differentiation at softer regions to produce a highly reproducible
structure (gjorevski2022).

#### Manipulating biochemical signaling

Another way of constructing epithelial structures is to control
biochemical signaling to induce shape transformation. It involves using
similar natural processes in embryo morphogenesis like an apical
constriction in ventral furrow formation or cell jamming in normal
elongation of the zebrafish. A localized apical constriction can be
controlled using optogenetic Rho signaling tools (izquierdo2018). Using
this technique, the furrow can be induced with spatial temporal control.
A similar technique of optogenetics can be used to target other proteins
such as Shroom3 to induce synthetic morphogenesis in neural organoids
(martinez-ara2022).

Tissue folding could also be triggered by epithelial-mesenchymal
interaction. Hughes et al. showed that cell clusters remodel the matrix
to create oriented stresses leading to budding in the tissues
(hughes2018). Engineering cell cluster locations and density allow for
controlling the curvature of the epithelia. The mesenchymal condensation
works as folding instructions for the final tissue structure
(palmquist2022, shyer2017).

The microenvironment plays a key role in providing vital signals to the
tissues, apart from the physical forces. Controlling these signals
allows for activating specific cellular functions engineering a tissue.
Newer microfluidic techniques can deliver appropriate morphogen gradient
to the tissue with precise timing (hofer2021s). In vivo, multiple
morphogens are acting simultaneously. For example, in vivo neural tube
development there is an opposing gradient of sonic hedgehog (SHH) and
bone morphogenic protein. With a microfluidic device stable gradient can
be generated, even in the opposite directions (demers2016). This can be
used to mimic symmetry-breaking events and directional neural tube
patterning.

However, the signaling could be controlled through the genetic
engineering of specific cells. Human pluripotent stem cells (hPSCs) can
be programmed to express SHH (cederquist2019). These cells when mixed
with others could result in a polarized organoid and results in a
patterned cerebral organoid.

#### Exploiting mechanical instabilities

Many morphogenetic processes include spontaneous pattern formation or
symmetry-breaking events (ishihara2018). Many of these are dictated by
mechanical instabilities. Usually, in material science, instabilities
are problematic because they cause large and rapid deformations causing
breakage. However, in soft matter, large deformations are possible and
lead to interesting topological transformations[^10]. This allows
engineers to exploit these instabilities to develop new actuators or
soft robots (reviewed in pal2021).

By comparing fluid splashes to hydroids, D\'Arcy Thompson foresaw the
importance of mechanical instabilities (thompson1979). He writes in the
context of shapes of a potter's cup, glass blowers blub, and biological
structures[^11]:

> "They are neither more nor less than glorified \"splashes,\" formed
> slowly, under conditions of restraint which enhance or reveal their
> mathematical symmetry."

His conjectures have been confirmed through numerous quantitative
studies on different systems: from ripples in leaves to wrinkles in the
brain (liang2009, karzbrun2018).

There are many instabilities associated with solids and fluids. For
example, Rayleigh-Plateau instability, explains the reason for the fluid
stream breaking up into smaller packets. It is driven by the tendency of
fluids to minimize the surface area because of the surface tension. The
same instability could arise if fluid is surrounded by an elastic medium
rather than air if and only if surface tensions can overcome the elastic
stresses. It could result in budding as seen in alveologenesis in human
mammary tissue (fernandez2021). As tissues are active viscoelastic
materials, the timescales of instabilities change. The process slows
down to hours compared to milliseconds of water droplets.

There are other instabilities such as Kelvin-Helmholtz instability;
Rayleigh-Taylor instability; Viscous coiling and folding; or largescale
wrinkling and buckling instability (reviewed in gallaire2017,
kourouklis2018). However, for us, the interest is to harness these
instabilities to recreate epithelial structures.

One of the prominent ways of inducing mechanical instabilities in solids
is compressive stresses. These stresses are ubiquitous in biological
systems and could arise through differential growth, swelling, or
morphogen gradients producing different forms of instabilities such as
wrinkling, creasing, and buckling.

Buckling phenomenon occurs when a thin sheet is subjected to the
compressive in-plane stress. If stresses are more than a critical amount
the whole sheet undergoes out of plane deformation instead of shrinking
in-plane. However, wrinkling/creasing/ridging occurs in similar
compressive stresses, but the thin sheet is typically supported by a
compliant substrate.

To recreate these phenomena in vitro, researchers have relied on
hydrogels. As mentioned earlier, typical organization of the biological
tissues is epithelia supported by a matrix. This could be represented by
thin film supported by a hydrogel. Particularly, to our interest
hydrogel can be mechanically and chemically controlled easily to
generate desired mechanical instabilities (reviewed in dervaux2012). We
could physically simulate growth through swelling or pre-stretching of
the gel; or manually apply compressive stresses.

During swelling, hydrogel undergoes drastic volumetric changes producing
transient crease-like patterns on the surface. The creases disappear
when gel reaches it full size. These folds could be made permanent on
the gel surface if the gel is constrained at the bottom. The
swelling-induced compressive stress build up at the free surface and
crease becomes permanent. However, if the constraint at the bottom is
another gel or flexible elastic substrate it will produce a wrinkling
instability. In comparison to previous case, in wrinkling instability
the folds have larger wavelength and eventually could make contact with
themselves. These instabilities are incredibly handy to understand many
systems from the wrinkled bread loaf to gyri-sulci of the brain cortex
(hohlfeld2011).

Tallinen and colleagues demonstrated that the brain cortex could be
replicated through programming material to produce wrinkling
(tallinen2016). They created a synthetic brain without folds with inner
core of inert elastomer and outer thin layer of swellable elastomer.
Inert part represents the white matter of the brain and outer layer the
cortical plate. On swelling it produces the folds closely matching the
gyrification process.

This is also reproduced in the growing embryonic airway epithelium on
top of a matrix. The growth of a thin film attached on the matrix
creates the stresses which produces the folds (varner2015). Similar
mechanism is shown to be at work in other systems with differential
growth as branching lungs, intestinal villi formation or gut looping
(kourouklis2018, shyer2013, savin2011). It is worth noting that these
studies point out an elegant physical mechanism to create these folds.
Although, this mechanism is widely contested in the developmental
biology.

Easier way of mimicking growth conditions is to directly stretch or
compress the gel. Chan et al. showed that by modulating the shear
modulus of the hydrogel with epithelial layer and stretch one can
control the patterns (chan2018). They stretch the hydrogel before
seeding cells and once cells are confluent into layer, they unstretch to
obtain folded pattern. The uniaxial prestretching predictably produces
oriented folded patterns. In contrast, the biaxial prestretching of the
cell-laden hydrogel produces various modes of patterns: from creases to
ridges closely resembling biological folds as intestinal villi. These
patterns are of different wavelengths due to the competition between
deformation of substrate and bending of the thin film: one prefers
shorter wavelength and other longer respectively.

The hydrogel or substrate could be encoded with mechanical information
of flexibility. As in case of prestretched membrane with a cell
monolayer on top; on cutting the membrane the tension in the monolayer
produces a curvature (tomba2022). Besides interaction with substrate,
stretching of epithelial layer devoid of matrix can produce curling
(fouchard2020).

Another form of instability in bilayers is delaminated buckling, where
the thin film buckles by delaminating from the substrate. It is widely
observed in the thin film delamination in furniture. In case of
epithelial tissue morphogenesis, compressive stresses can be created to
growth or collective tension. Trusko et al. show that the growing
epithelia confined in a sphere undergoes delaminated buckling after
reaching critical growth induced stress (trusko2020). Same outcome can
be achieved with intercellular stresses. If the deformation of the
substrate is controlled in certain region; cell monolayer is tension is
enough to delaminate and create a fold (oyama2021). Even more
interesting approach taken by Cont et al., where they put biofilm on top
of the epithelial monolayer leading to compressive stresses causing
delaminated folds (cont2020).

Additionally, ventral furrow formation of drosophila embryo could also
be looked as a buckling event. There are multiple explanations including
apical constriction, basal expansion, or cell crowding (reviewed in
martin2020). And yet, are they necessary or sufficient conditions to
undergo mesoderm invagination. Recent studies show that the embryo level
forces cause instability leading to the fold (guo2022, fierling2022).

It is worth noting that there is only one method to directly apply
compressive stresses and induce buckling in suspended epithelial tissue.
Lab of Guillaume Charras use cell laden collagen gel between two rods,
where the gel is digested with collagenase to create a suspended
monolayer (harris2012). They observed that the compression of more than
35% strain produced transient buckling events (wyatt2020). The actin
cytoskeleton plays a key role in buffering the deformations.

### Tissue Hydraulics

#### Hydraulic control of tissue patterning

In this thesis, we will be concentrating on the role of hydraulic
pressure in guiding morphogenesis. Notably, lumens expansion in
developmental biology is driven by fluid pressure. In mouse embryo, cell
aggregate establishes small fluid cavities in intercellular junctions.
These microlumens are unstable; powered by osmotic pressure gradient
they grow and coalesce into a large lumen breaking the embryo symmetry.
The cells pump ions and water and generate a pressure in these
fluid-filled cavities. Thus, giving rise to spherical embryo. The
pressure relates to the curvature and surface tension through Laplace
law.

\$\$ \\sigma = \\frac{\\Delta P R}{2} \$\$

The shape created under pressure depends on the material properties of
the tissue. Homogeneous material would create uniform curvature like
spherical shape. However, oriented cells or anisotropic tissue would
lead to various shapes like cylinders or ellipsoids. Interestingly,
lizard lungs have a lobed epithelium which resembles a stress ball
shape. Palmer et al. propose that the smooth muscle network constrains
the epithelia like mesh around a stress ball. On pressure application,
epithelium inflates in regions in the gaps of muscles.

For embryos, when pressure increases the tension increases and cells
stretch. After certain threshold cell junctions may leak during the
division and the luminal pressure reduces causing embryonic cavity to
shrink. This system of pressure and leakage acts as a size regulation
mechanism. At the same time, it polarizes the embryo and promotes cell
segregation by fate specification.

Similar coalescence and lumen coarsening is also observed in other
systems such as zebrafish gut, otic vesicle, or salivary glands. The
pressure can also be built up through secretion of the matrix as in the
case of the drosophila hindgut with mucins. In the same way, secretion
of hyaluronic acid forms the buds leading to formation of the ear canals
in zebrafish otic vesicle.

#### Mechanics of domes

### What is to be done?

The principles which govern tissue form and function are very important;
on two fronts. First, to understand fundamental physical rules of
biology, and second for inspiration of new engineering tools and design
principles. We want to use state-of-the-art technologies such as
bioprinting, microfluidics, and 3D cell cultures to control
morphogenetic driving factors individually; allowing us to test tissues
from the material science point of view. This specific probing allows us
to comprehend the intricate mechanism of the generation of forces, and
shape change at the cellular and tissue levels. Using a microfluidic
setup, we subject tissues to unravel emergent phenomena at different
spatial and temporal scales.

This is a process of deformation or growth of the tissue under the
combination of endogenous and exogenous mechanical forces that include
contractility of the epithelium itself and the surrounding matrix as
well as hydraulic pressure from the lumen. These stresses are applied to
different material components of the tissues, such as cells and the
extracellular matrix, that display distinct viscoelastic properties and
remodeling time scales. Understanding how the complex interplay between
tissue stresses and viscoelastic properties gives rise to specific
morphogenetic events in vivo poses outstanding technical and conceptual
challenges. These include difficulties to disentangle the relative role
of the distinct components involved in a system, the lack of tools for
quantitative measurements of stresses and mechanical properties, and the
inability to impose controlled stresses over a broad range of amplitudes
and rates. As a complementary strategy, bottom-up approaches aim at
understanding the role of each component of the system and its
morphogenetic potential, with the ultimate goal of building complexity
through rational engineering of the building blocks that form functional
tissue. These approaches have been successful at engineering elementary
morphogenetic processes such as epithelial bending or buckling. However,
despite the emerging success of bottom-up approaches, we still lack
tools to simultaneously measure and control the shape and stress of 3D
epithelia. In addition, we lack computational models that integrate
cellular and tissue shape with the subcellular determinants of
epithelial mechanics such as the contractility, turnover, and
viscoelasticity of the actomyosin cortex.

Here we present a microfluidic-based technique to impose a controlled
deformation on an epithelial monolayer while continuously monitoring its
state of stress. With this technique, we probe the active
viscoelasticity of epithelial layers over a range of physiological time
scales. We present a 3D model of the epithelium, which shows that the
observed phenomenology can be explained by the active viscoelastic
properties of the actomyosin cortex. Finally, we show that these
viscoelastic properties combined with adhesion micropatterning can be
harnessed to engineer epithelial wrinkles of predicted geometry.

## References

'A ton for Thompson's tome' (2017) *Nature Physics*, 13(4), pp.
315--315. Available at: <https://doi.org/10.1038/nphys4096>.

Alberts, B. (2015) *Molecular biology of the cell*. Sixth edition. New
York, NY: Garland Science, Taylor and Francis Group.

Alt, S., Ganguly, P. and Salbreux, G. (2017) 'Vertex models: from cell
mechanics to tissue morphogenesis', *Philosophical Transactions of the
Royal Society B: Biological Sciences*, 372(1720), p. 20150520. Available
at: <https://doi.org/10.1098/rstb.2015.0520>.

*Are All Fish the Same Shape if You Stretch Them? The Victorian Tale of
On Growth and Form* (no date). Available at:
<https://writings.stephenwolfram.com/2017/10/are-all-fish-the-same-shape-if-you-stretch-them-the-victorian-tale-of-on-growth-and-form/>.

Balasubramaniam, L. *et al.* (2021) 'Investigating the nature of active
forces in tissues reveals how contractile cells can form extensile
monolayers', *Nature Materials*, 20(8), pp. 1156--1166. Available at:
<https://doi.org/10.1038/s41563-021-00919-2>.

Bao, G. and Suresh, S. (2003) 'Cell and molecular mechanics of
biological materials', *Nature Materials*, 2(11), pp. 715--725.
Available at: <https://doi.org/10.1038/nmat1001>.

Barker, N. (2014) 'Adult intestinal stem cells: critical drivers of
epithelial homeostasis and regeneration', *Nature Reviews Molecular Cell
Biology*, 15(1), pp. 19--33. Available at:
<https://doi.org/10.1038/nrm3721>.

Braga, V. (2016) 'Spatial integration of E-cadherin adhesion, signalling
and the epithelial cytoskeleton', *Current Opinion in Cell Biology*, 42,
pp. 138--145. Available at: <https://doi.org/10.1016/j.ceb.2016.07.006>.

Brassard, J.A. *et al.* (2021) 'Recapitulating macro-scale tissue
self-organization through organoid bioprinting', *Nature Materials*,
20(1), pp. 22--29. Available at:
<https://doi.org/10.1038/s41563-020-00803-5>.

Breau, K.A. *et al.* (2022) 'Efficient transgenesis and
homology-directed gene targeting in monolayers of primary human small
intestinal and colonic epithelial stem cells', *Stem Cell Reports*,
17(6), pp. 1493--1506. Available at:
<https://doi.org/10.1016/j.stemcr.2022.04.005>.

Brown, T.M. and Fee, E. (2006) 'Rudolf Carl Virchow', *American Journal
of Public Health*, 96(12), pp. 2104--2105. Available at:
<https://doi.org/10.2105/AJPH.2005.078436>.

Brugués, A. *et al.* (2014) 'Forces driving epithelial wound healing',
*Nature Physics*, 10(9), pp. 683--690. Available at:
<https://doi.org/10.1038/nphys3040>.

Bryant, D.M. and Mostov, K.E. (2008) 'From cells to organs: building
polarized tissue', *Nature Reviews Molecular Cell Biology*, 9(11), pp.
887--901. Available at: <https://doi.org/10.1038/nrm2523>.

Calzolari, S., Terriente, J. and Pujades, C. (2014) 'Cell segregation in
the vertebrate hindbrain relies on actomyosin cables located at the
interhombomeric boundaries', *The EMBO Journal*, 33(7), pp. 686--701.
Available at: <https://doi.org/10.1002/embj.201386003>.

Campàs, O. *et al.* (2014) 'Quantifying cell-generated mechanical forces
within living embryonic tissues', *Nature Methods*, 11(2), pp. 183--189.
Available at: <https://doi.org/10.1038/nmeth.2761>.

Carlier, F.M., de Fays, C. and Pilette, C. (2021) 'Epithelial Barrier
Dysfunction in Chronic Respiratory Diseases', *Frontiers in Physiology*,
12. Available at:
<https://www.frontiersin.org/articles/10.3389/fphys.2021.691227>
(Accessed: 23 December 2022).

Cartagena-Rivera, A.X. *et al.* (2016) 'Actomyosin Cortical Mechanical
Properties in Nonadherent Cells Determined by Atomic Force Microscopy',
*Biophysical Journal*, 110(11), pp. 2528--2539. Available at:
<https://doi.org/10.1016/j.bpj.2016.04.034>.

Casares, L. *et al.* (2015) 'Hydraulic fracture during epithelial
stretching', *Nature Materials*, 14(3), pp. 343--351. Available at:
<https://doi.org/10.1038/nmat4206>.

Cetera, M. *et al.* (2014) 'Epithelial rotation promotes the global
alignment of contractile actin bundles during Drosophila egg chamber
elongation', *Nature Communications*, 5(1), p. 5511. Available at:
<https://doi.org/10.1038/ncomms6511>.

Chan, C.J. *et al.* (2019) 'Hydraulic control of mammalian embryo size
and cell fate', *Nature*, 571(7763), pp. 112--116. Available at:
<https://doi.org/10.1038/s41586-019-1309-x>.

Chan, C.J. and Hiiragi, T. (2020) 'Integration of luminal pressure and
signalling in tissue self-organization', *Development*, 147(5), p.
dev181297. Available at: <https://doi.org/10.1242/dev.181297>.

Choudhury, M.I. *et al.* (2022) 'Kidney epithelial cells are active
mechano-biological fluid pumps', *Nature Communications*, 13(1), p.
2317. Available at: <https://doi.org/10.1038/s41467-022-29988-w>.

Clarke, D.N. and Martin, A.C. (2021) 'Actin-based force generation and
cell adhesion in tissue morphogenesis', *Current Biology*, 31(10), pp.
R667--R680. Available at: <https://doi.org/10.1016/j.cub.2021.03.031>.

Collinet, C. *et al.* (2015) 'Local and tissue-scale forces drive
oriented junction growth during tissue extension', *Nature Cell
Biology*, 17(10), pp. 1247--1258. Available at:
<https://doi.org/10.1038/ncb3226>.

Collinet, C. and Lecuit, T. (2021) 'Programmed and self-organized flow
of information during morphogenesis', *Nature Reviews Molecular Cell
Biology*, 22(4), pp. 245--265. Available at:
<https://doi.org/10.1038/s41580-020-00318-6>.

Deforet, M. *et al.* (2014) 'Emergence of collective modes and
tri-dimensional structures from epithelial confinement', *Nature
Communications*, 5(1), p. 3747. Available at:
<https://doi.org/10.1038/ncomms4747>.

Dolega, M.E. *et al.* (2017) 'Cell-like pressure sensors reveal increase
of mechanical stress towards the core of multicellular spheroids under
compression', *Nature Communications*, 8(1), p. 14056. Available at:
<https://doi.org/10.1038/ncomms14056>.

Ducuing, A. and Vincent, S. (2016) 'The actin cable is dispensable in
directing dorsal closure dynamics but neutralizes mechanical stress to
prevent scarring in the Drosophila embryo', *Nature Cell Biology*,
18(11), pp. 1149--1160. Available at: <https://doi.org/10.1038/ncb3421>.

Dumortier, J.G. *et al.* (2019) 'Hydraulic fracturing and active
coarsening position the lumen of the mouse blastocyst', *Science*
\[Preprint\]. Available at: <https://doi.org/10.1126/science.aaw7709>.

Duque, J. *et al.* (2023) 'Fracture in Living Cell Monolayers'. bioRxiv,
p. 2023.01.05.522736. Available at:
<https://doi.org/10.1101/2023.01.05.522736>.

Eisenhoffer, G.T. and Rosenblatt, J. (2013) 'Bringing balance by force:
live cell extrusion controls epithelial cell numbers', *Trends in Cell
Biology*, 23(4), pp. 185--192. Available at:
<https://doi.org/10.1016/j.tcb.2012.11.006>.

Elosegui-Artola, A. *et al.* (2016) 'Mechanical regulation of a
molecular clutch defines force transmission and transduction in response
to matrix rigidity', *Nature Cell Biology*, 18(5), pp. 540--548.
Available at: <https://doi.org/10.1038/ncb3336>.

Elosegui-Artola, A. *et al.* (2017) 'Force Triggers YAP Nuclear Entry by
Regulating Transport across Nuclear Pores', *Cell*, 171(6), pp.
1397-1410.e14. Available at:
<https://doi.org/10.1016/j.cell.2017.10.008>.

Elosegui-Artola, A. *et al.* (2022) 'Matrix viscoelasticity controls
spatiotemporal tissue organization', *Nature Materials*, pp. 1--11.
Available at: <https://doi.org/10.1038/s41563-022-01400-4>.

Engler, A.J. *et al.* (2006) 'Matrix Elasticity Directs Stem Cell
Lineage Specification', *Cell*, 126(4), pp. 677--689. Available at:
<https://doi.org/10.1016/j.cell.2006.06.044>.

Fasano, A. *et al.* (1991) 'Vibrio cholerae produces a second
enterotoxin, which affects intestinal tight junctions.', *Proceedings of
the National Academy of Sciences*, 88(12), pp. 5242--5246. Available at:
<https://doi.org/10.1073/pnas.88.12.5242>.

Firmin, J. *et al.* (2022) 'Mechanics of human embryo compaction'.
bioRxiv, p. 2022.01.09.475429. Available at:
<https://doi.org/10.1101/2022.01.09.475429>.

Fletcher, D.A. and Mullins, R.D. (2010) 'Cell mechanics and the
cytoskeleton', *Nature*, 463(7280), pp. 485--492. Available at:
<https://doi.org/10.1038/nature08908>.

Fortunato, I.C. and Sunyer, R. (2022) 'The Forces behind Directed Cell
Migration', *Biophysica*, 2(4), pp. 548--563. Available at:
<https://doi.org/10.3390/biophysica2040046>.

Gjorevski, N. *et al.* (2016) 'Designer matrices for intestinal stem
cell and organoid culture', *Nature*, 539(7630), pp. 560--564. Available
at: <https://doi.org/10.1038/nature20168>.

Gjorevski, N. *et al.* (2022) 'Tissue geometry drives deterministic
organoid patterning', *Science* \[Preprint\]. Available at:
<https://doi.org/10.1126/science.aaw9021>.

Godard, B.G. and Heisenberg, C.-P. (2019) 'Cell division and tissue
mechanics', *Current Opinion in Cell Biology*, 60, pp. 114--120.
Available at: <https://doi.org/10.1016/j.ceb.2019.05.007>.

Gómez-Gálvez, P. *et al.* (2021) 'The complex three-dimensional
organization of epithelial tissues', *Development*, 148(1), p.
dev195669. Available at: <https://doi.org/10.1242/dev.195669>.

Gómez-González, M. *et al.* (2020) 'Measuring mechanical stress in
living tissues', *Nature Reviews Physics*, 2(6), pp. 300--317. Available
at: <https://doi.org/10.1038/s42254-020-0184-6>.

Gorfinkiel, N. and Martinez Arias, A. (2021) 'The cell in the age of the
genomic revolution: Cell Regulatory Networks', *Cells & Development*,
168, p. 203720. Available at:
<https://doi.org/10.1016/j.cdev.2021.203720>.

Guillamat, P. *et al.* (2022) 'Integer topological defects organize
stresses driving tissue morphogenesis', *Nature Materials*, 21(5), pp.
588--597. Available at: <https://doi.org/10.1038/s41563-022-01194-5>.

Guillot, C. and Lecuit, T. (2013) 'Mechanics of Epithelial Tissue
Homeostasis and Morphogenesis', *Science*, 340(6137), pp. 1185--1189.
Available at: <https://doi.org/10.1126/science.1235249>.

Gutzman, J.H. *et al.* (2018) 'Basal constriction during
midbrain--hindbrain boundary morphogenesis is mediated by Wnt5b and
focal adhesion kinase', *Biology Open*, 7(11), p. bio034520. Available
at: <https://doi.org/10.1242/bio.034520>.

Guyon, J. *et al.* (2021) 'Co-culture of Glioblastoma Stem-like Cells on
Patterned Neurons to Study Migration and Cellular Interactions',
*Journal of Visualized Experiments*, (168), p. 62213. Available at:
<https://doi.org/10.3791/62213>.

Haigo, S.L. and Bilder, D. (2011) 'Global Tissue Revolutions in a
Morphogenetic Movement Controlling Elongation', *Science*, 331(6020),
pp. 1071--1074. Available at: <https://doi.org/10.1126/science.1199424>.

Harris, A.K., Wild, P. and Stopak, D. (1980) 'Silicone Rubber Substrata:
A New Wrinkle in the Study of Cell Locomotion', *Science*, 208(4440),
pp. 177--179. Available at: <https://doi.org/10.1126/science.6987736>.

Harris, A.R. *et al.* (2012) 'Characterizing the mechanics of cultured
cell monolayers', *Proceedings of the National Academy of Sciences*,
109(41), pp. 16449--16454. Available at:
<https://doi.org/10.1073/pnas.1213301109>.

Hatzfeld, M., Keil, R. and Magin, T.M. (2017) 'Desmosomes and
Intermediate Filaments: Their Consequences for Tissue Mechanics', *Cold
Spring Harbor Perspectives in Biology*, 9(6), p. a029157. Available at:
<https://doi.org/10.1101/cshperspect.a029157>.

Heer, N.C. and Martin, A.C. (2017) 'Tension, contraction and tissue
morphogenesis', *Development*, 144(23), pp. 4249--4260. Available at:
<https://doi.org/10.1242/dev.151282>.

Helm, P. *et al.* (2005) 'Measuring and Mapping Cardiac Fiber and
Laminar Architecture Using Diffusion Tensor MR Imaging', *Annals of the
New York Academy of Sciences*, 1047(1), pp. 296--307. Available at:
<https://doi.org/10.1196/annals.1341.026>.

Hofer, M. and Lutolf, M.P. (2021) 'Engineering organoids', *Nature
Reviews Materials*, 6(5), pp. 402--420. Available at:
<https://doi.org/10.1038/s41578-021-00279-y>.

Houssin, N.S. *et al.* (2020) 'Formation and contraction of
multicellular actomyosin cables facilitate lens placode invagination',
*Developmental Biology*, 462(1), pp. 36--49. Available at:
<https://doi.org/10.1016/j.ydbio.2020.02.014>.

Huh, D. *et al.* (2010) 'Reconstituting Organ-Level Lung Functions on a
Chip', *Science*, 328(5986), pp. 1662--1668. Available at:
<https://doi.org/10.1126/science.1188302>.

Humphrey, J.D. (2002) *Cardiovascular Solid Mechanics*. New York, NY:
Springer New York. Available at:
<https://doi.org/10.1007/978-0-387-21576-1>.

Humphrey, J.D., Dufresne, E.R. and Schwartz, M.A. (2014)
'Mechanotransduction and extracellular matrix homeostasis', *Nature
Reviews Molecular Cell Biology*, 15(12), pp. 802--812. Available at:
<https://doi.org/10.1038/nrm3896>.

Ingber, D.E. (2018) 'From mechanobiology to developmentally inspired
engineering', *Philosophical Transactions of the Royal Society B:
Biological Sciences*, 373(1759), p. 20170323. Available at:
<https://doi.org/10.1098/rstb.2017.0323>.

Ishiguro, T. *et al.* (2017) 'Tumor-derived spheroids: Relevance to
cancer stem cells and clinical applications', *Cancer Science*, 108(3),
pp. 283--289. Available at: <https://doi.org/10.1111/cas.13155>.

Karzbrun, E. *et al.* (2021) 'Human neural tube morphogenesis in vitro
by geometric constraints', *Nature*, 599(7884), pp. 268--272. Available
at: <https://doi.org/10.1038/s41586-021-04026-9>.

Kechagia, J.Z., Ivaska, J. and Roca-Cusachs, P. (2019) 'Integrins as
biomechanical sensors of the microenvironment', *Nature Reviews
Molecular Cell Biology*, 20(8), pp. 457--473. Available at:
<https://doi.org/10.1038/s41580-019-0134-2>.

Kim, E.J.Y., Korotkevich, E. and Hiiragi, T. (2018) 'Coordination of
Cell Polarity, Mechanics and Fate in Tissue Self-organization', *Trends
in Cell Biology*, 28(7), pp. 541--550. Available at:
<https://doi.org/10.1016/j.tcb.2018.02.008>.

Kumar, A., Placone, J.K. and Engler, A.J. (2017) 'Understanding the
extracellular forces that determine cell fate and maintenance',
*Development*, 144(23), pp. 4261--4270. Available at:
<https://doi.org/10.1242/dev.158469>.

Labernadie, A. and Trepat, X. (2018) 'Sticking, steering, squeezing and
shearing: cell movements driven by heterotypic mechanical forces',
*Current Opinion in Cell Biology*, 54, pp. 57--65. Available at:
<https://doi.org/10.1016/j.ceb.2018.04.008>.

Latorre, E. *et al.* (2018) 'Active superelasticity in three-dimensional
epithelia of controlled shape', *Nature*, 563(7730), pp. 203--208.
Available at: <https://doi.org/10.1038/s41586-018-0671-4>.

Lecuit, T., Lenne, P.-F. and Munro, E. (2011) 'Force Generation,
Transmission, and Integration during Cell and Tissue Morphogenesis',
*Annual Review of Cell and Developmental Biology*, 27(1), pp. 157--184.
Available at: <https://doi.org/10.1146/annurev-cellbio-100109-104027>.

Lever, J.E. (1979) 'Regulation of dome formation in differentiated
epithelial cell cultures', *Journal of Supramolecular Structure*, 12(2),
pp. 259--272. Available at: <https://doi.org/10.1002/jss.400120210>.

Lomakin, A.J. *et al.* (2020) 'The nucleus acts as a ruler tailoring
cell responses to spatial constraints', *Science*, 370(6514), p.
eaba2894. Available at: <https://doi.org/10.1126/science.aba2894>.

Luciano, M. *et al.* (2021) 'Cell monolayers sense curvature by
exploiting active mechanics and nuclear mechanoadaptation', *Nature
Physics*, 17(12), pp. 1382--1390. Available at:
<https://doi.org/10.1038/s41567-021-01374-1>.

MacCord, K. (2012) 'Epithelium'. Available at:
<https://hpsrepository.asu.edu/handle/10776/3946> (Accessed: 19 December
2022).

Malandrino, A. *et al.* (2018) 'Complex mechanics of the heterogeneous
extracellular matrix in cancer', *Extreme Mechanics Letters*, 21, pp.
25--34. Available at: <https://doi.org/10.1016/j.eml.2018.02.003>.

Marchiando, A.M., Graham, W.V. and Turner, J.R. (2010) 'Epithelial
Barriers in Homeostasis and Disease', *Annual Review of Pathology:
Mechanisms of Disease*, 5(1), pp. 119--144. Available at:
<https://doi.org/10.1146/annurev.pathol.4.110807.092135>.

Marín-Llauradó, A. *et al.* (2022) 'Mapping mechanical stress in curved
epithelia of designed size and shape'. bioRxiv, p. 2022.05.03.490382.
Available at: <https://doi.org/10.1101/2022.05.03.490382>.

Maroudas-Sacks, Y. *et al.* (2021) 'Topological defects in the nematic
order of actin fibres as organization centres of Hydra morphogenesis',
*Nature Physics*, 17(2), pp. 251--259. Available at:
<https://doi.org/10.1038/s41567-020-01083-1>.

Martin, A.C., Kaschube, M. and Wieschaus, E.F. (2009) 'Pulsed
contractions of an actin--myosin network drive apical constriction',
*Nature*, 457(7228), pp. 495--499. Available at:
<https://doi.org/10.1038/nature07522>.

Martínez-Ara, G. *et al.* (2022) 'Optogenetic control of apical
constriction induces synthetic morphogenesis in mammalian tissues',
*Nature Communications*, 13(1), p. 5400. Available at:
<https://doi.org/10.1038/s41467-022-33115-0>.

Mertz, A.F. *et al.* (2013) 'Cadherin-based intercellular adhesions
organize epithelial cell--matrix traction forces', *Proceedings of the
National Academy of Sciences*, 110(3), pp. 842--847. Available at:
<https://doi.org/10.1073/pnas.1217279110>.

Mofrad, M.R.K. (2009) 'Rheology of the Cytoskeleton', *Annual Review of
Fluid Mechanics*, 41(1), pp. 433--453. Available at:
<https://doi.org/10.1146/annurev.fluid.010908.165236>.

Mongera, A. *et al.* (2023) 'Mechanics of the cellular microenvironment
as probed by cells in vivo during zebrafish presomitic mesoderm
differentiation', *Nature Materials*, 22(1), pp. 135--143. Available at:
<https://doi.org/10.1038/s41563-022-01433-9>.

Monier, B. *et al.* (2015) 'Apico-basal forces exerted by apoptotic
cells drive epithelium folding', *Nature*, 518(7538), pp. 245--248.
Available at: <https://doi.org/10.1038/nature14152>.

Morizane, R. and Bonventre, J.V. (2017) 'Generation of nephron
progenitor cells and kidney organoids from human pluripotent stem
cells', *Nature Protocols*, 12(1), pp. 195--207. Available at:
<https://doi.org/10.1038/nprot.2016.170>.

Mullin, J.M. *et al.* (2005) 'Keynote review: Epithelial and endothelial
barriers in human disease', *Drug Discovery Today*, 10(6), pp. 395--408.
Available at: <https://doi.org/10.1016/S1359-6446(05)03379-9>.

Muncie, J.M. *et al.* (2020) 'Mechanical Tension Promotes Formation of
Gastrulation-like Nodes and Patterns Mesoderm Specification in Human
Embryonic Stem Cells', *Developmental Cell*, 55(6), pp. 679-694.e11.
Available at: <https://doi.org/10.1016/j.devcel.2020.10.015>.

Nelson, C.M. *et al.* (2005) 'Emergent patterns of growth controlled by
multicellular form and mechanics', *Proceedings of the National Academy
of Sciences*, 102(33), pp. 11594--11599. Available at:
<https://doi.org/10.1073/pnas.0502575102>.

Nelson, C.M. *et al.* (2017) 'Microfluidic chest cavities reveal that
transmural pressure controls the rate of lung development',
*Development*, 144(23), pp. 4328--4335. Available at:
<https://doi.org/10.1242/dev.154823>.

Nelson, C.M., Inman, J.L. and Bissell, M.J. (2008) 'Three-dimensional
lithographically defined organotypic tissue arrays for quantitative
analysis of morphogenesis and neoplastic progression', *Nature
Protocols*, 3(4), pp. 674--678. Available at:
<https://doi.org/10.1038/nprot.2008.35>.

Odell, G.M. *et al.* (1981) 'The mechanical basis of morphogenesis',
*Developmental Biology*, 85(2), pp. 446--462. Available at:
<https://doi.org/10.1016/0012-1606(81)90276-1>.

Okuda, S. *et al.* (2018) 'Strain-triggered mechanical feedback in
self-organizing optic-cup morphogenesis', *Science Advances*, 4(11), p.
eaau1354. Available at: <https://doi.org/10.1126/sciadv.aau1354>.

Oriola, D. *et al.* (2022) 'Arrested coalescence of multicellular
aggregates', *Soft Matter*, 18(19), pp. 3771--3780. Available at:
<https://doi.org/10.1039/D2SM00063F>.

Özgüç, Ö. *et al.* (2022) 'Cortical softening elicits zygotic
contractility during mouse preimplantation development', *PLOS Biology*,
20(3), p. e3001593. Available at:
<https://doi.org/10.1371/journal.pbio.3001593>.

Pallarès, M.E. *et al.* (2022) 'Stiffness-dependent active wetting
enables optimal collective cell durotaxis', *Nature Physics*, pp. 1--11.
Available at: <https://doi.org/10.1038/s41567-022-01835-1>.

Palmer, M.A. *et al.* (2021) 'Stress ball morphogenesis: How the lizard
builds its lung', *Science Advances*, 7(52), p. eabk0161. Available at:
<https://doi.org/10.1126/sciadv.abk0161>.

Pérez-González, C. *et al.* (2019) 'Active wetting of epithelial
tissues', *Nature Physics*, 15(1), pp. 79--88. Available at:
<https://doi.org/10.1038/s41567-018-0279-5>.

Pérez-González, C. *et al.* (2021) 'Mechanical compartmentalization of
the intestinal organoid enables crypt folding and collective cell
migration', *Nature Cell Biology*, 23(7), pp. 745--757. Available at:
<https://doi.org/10.1038/s41556-021-00699-6>.

Prahl, L.S. *et al.* (2022) 'Independent control over cell patterning
and adhesion on hydrogel substrates for tissue interface
mechanobiology'. bioRxiv, p. 2022.11.16.516785. Available at:
<https://doi.org/10.1101/2022.11.16.516785>.

Roca-Cusachs, P., Conte, V. and Trepat, X. (2017) 'Quantifying forces in
cell biology', *Nature Cell Biology*, 19(7), pp. 742--751. Available at:
<https://doi.org/10.1038/ncb3564>.

Samal, P. *et al.* (2019) 'Grow with the Flow: When Morphogenesis Meets
Microfluidics', *Advanced Materials*, 31(17), p. 1805764. Available at:
<https://doi.org/10.1002/adma.201805764>.

Sances, S. *et al.* (2018) 'Human iPSC-Derived Endothelial Cells and
Microengineered Organ-Chip Enhance Neuronal Development', *Stem Cell
Reports*, 10(4), pp. 1222--1236. Available at:
<https://doi.org/10.1016/j.stemcr.2018.02.012>.

Schamberger, B. *et al.* (2022) 'Curvature in biological systems: its
quantification, emergence and implications across the scales', *Advanced
Materials*, p. e2206110.

Schöck, F. and Perrimon, N. (2002) 'Molecular Mechanisms of Epithelial
Morphogenesis', *Annual Review of Cell and Developmental Biology*,
18(1), pp. 463--493. Available at:
<https://doi.org/10.1146/annurev.cellbio.18.022602.131838>.

Serra-Picamal, X. *et al.* (2012) 'Mechanical waves during tissue
expansion', *Nature Physics*, 8(8), pp. 628--634. Available at:
<https://doi.org/10.1038/nphys2355>.

Serwane, F. *et al.* (2017) 'In vivo quantification of spatially varying
mechanical properties in developing tissues', *Nature Methods*, 14(2),
pp. 181--186. Available at: <https://doi.org/10.1038/nmeth.4101>.

Shah, G. *et al.* (2019) 'Multi-scale imaging and analysis identify
pan-embryo cell dynamics of germlayer formation in zebrafish', *Nature
Communications*, 10(1), p. 5753. Available at:
<https://doi.org/10.1038/s41467-019-13625-0>.

Shellard, A. and Mayor, R. (2021) 'Collective durotaxis along a
self-generated stiffness gradient in vivo', *Nature*, 600(7890), pp.
690--694. Available at: <https://doi.org/10.1038/s41586-021-04210-x>.

Shyer, A.E. *et al.* (2013) 'Villification: How the Gut Gets Its Villi',
*Science*, 342(6155), pp. 212--218. Available at:
<https://doi.org/10.1126/science.1238842>.

Sidhaye, J. and Norden, C. (2017) 'Concerted action of neuroepithelial
basal shrinkage and active epithelial migration ensures efficient optic
cup morphogenesis', *eLife*. Edited by D.Y. Stainier, 6, p. e22689.
Available at: <https://doi.org/10.7554/eLife.22689>.

Stanton, A.E., Tong, X. and Yang, F. (2019) 'Extracellular matrix type
modulates mechanotransduction of stem cells', *Acta Biomaterialia*, 96,
pp. 310--320. Available at:
<https://doi.org/10.1016/j.actbio.2019.06.048>.

Sui, L. *et al.* (2018) 'Differential lateral and basal tension drive
folding of Drosophila wing discs through two distinct mechanisms',
*Nature Communications*, 9(1), p. 4620. Available at:
<https://doi.org/10.1038/s41467-018-06497-3>.

Sunyer, R. *et al.* (2016) 'Collective cell durotaxis emerges from
long-range intercellular force transmission', *Science*, 353(6304), pp.
1157--1161. Available at: <https://doi.org/10.1126/science.aaf7119>.

Tallinen, T. *et al.* (2016) 'On the growth and form of cortical
convolutions', *Nature Physics*, 12(6), pp. 588--593. Available at:
<https://doi.org/10.1038/nphys3632>.

Tambe, D.T. *et al.* (2011) 'Collective cell guidance by cooperative
intercellular forces', *Nature Materials*, 10(6), pp. 469--475.
Available at: <https://doi.org/10.1038/nmat3025>.

Tang, W. *et al.* (2022) 'Collective curvature sensing and fluidity in
three-dimensional multicellular systems', *Nature Physics*, 18(11), pp.
1371--1378. Available at: <https://doi.org/10.1038/s41567-022-01747-0>.

'The 100-year-old challenge to Darwin that is still making waves in
research' (2017) *Nature*, 544(7649), pp. 138--139. Available at:
<https://doi.org/10.1038/544138a>.

Thiery, J.P. *et al.* (2009) 'Epithelial-Mesenchymal Transitions in
Development and Disease', *Cell*, 139(5), pp. 871--890. Available at:
<https://doi.org/10.1016/j.cell.2009.11.007>.

Thompson, D.W. (1979) *On Growth and form*. Repr. Cambridge: Univ. Pr.

Tlili, S. *et al.* (2018) 'Collective cell migration without
proliferation: density determines cell velocity and wave velocity',
*Royal Society Open Science*, 5(5), p. 172421. Available at:
<https://doi.org/10.1098/rsos.172421>.

Torras, N. *et al.* (2018) 'Mimicking Epithelial Tissues in
Three-Dimensional Cell Culture Models', *Frontiers in Bioengineering and
Biotechnology*, 6. Available at:
<https://www.frontiersin.org/articles/10.3389/fbioe.2018.00197>
(Accessed: 10 January 2023).

Trepat, X. and Sahai, E. (2018) 'Mesoscale physical principles of
collective cell organization', *Nature Physics*, 14(7), pp. 671--682.
Available at: <https://doi.org/10.1038/s41567-018-0194-9>.

Valon, L. *et al.* (2017) 'Optogenetic control of cellular forces and
mechanotransduction', *Nature Communications*, 8(1), p. 14396. Available
at: <https://doi.org/10.1038/ncomms14396>.

Varner, V.D. *et al.* (2015) 'Mechanically patterning the embryonic
airway epithelium', *Proceedings of the National Academy of Sciences*,
112(30), pp. 9230--9235. Available at:
<https://doi.org/10.1073/pnas.1504102112>.

Vedula, S.R.K. *et al.* (2012) 'Emerging modes of collective cell
migration induced by geometrical constraints', *Proceedings of the
National Academy of Sciences*, 109(32), pp. 12974--12979. Available at:
<https://doi.org/10.1073/pnas.1119313109>.

Veenvliet, J.V. *et al.* (2021) 'Sculpting with stem cells: how models
of embryo development take shape', *Development*, 148(24), p. dev192914.
Available at: <https://doi.org/10.1242/dev.192914>.

Venturini, V. *et al.* (2020) 'The nucleus measures shape changes for
cellular proprioception to control dynamic cell behavior', *Science*,
370(6514), p. eaba2644. Available at:
<https://doi.org/10.1126/science.aba2644>.

Vianello, S. and Lutolf, M.P. (2019) 'Understanding the Mechanobiology
of Early Mammalian Development through Bioengineered Models',
*Developmental Cell*, 48(6), pp. 751--763. Available at:
<https://doi.org/10.1016/j.devcel.2019.02.024>.

Vignaud, T., Blanchoin, L. and Théry, M. (2012) 'Directed cytoskeleton
self-organization', *Trends in Cell Biology*, 22(12), pp. 671--682.
Available at: <https://doi.org/10.1016/j.tcb.2012.08.012>.

Virchow, R. *et al.* (1860) *Cellular pathology as based upon
physiological and pathological histology; twenty lectures delivered in
the Pathological Institute of Berlin during the months of February,
March, and April, 1858*. London: John Churchill, pp. 1--546. Available
at: <https://doi.org/10.5962/bhl.title.110759>.

Wagh, K. *et al.* (2021) 'Mechanical Regulation of Transcription: Recent
Advances', *Trends in Cell Biology*, 31(6), pp. 457--472. Available at:
<https://doi.org/10.1016/j.tcb.2021.02.008>.

Walma, D.A.C. and Yamada, K.M. (2020) 'The extracellular matrix in
development', *Development*, 147(10), p. dev175596. Available at:
<https://doi.org/10.1242/dev.175596>.

Warmflash, A. *et al.* (2014) 'A method to recapitulate early embryonic
spatial patterning in human embryonic stem cells', *Nature Methods*,
11(8), pp. 847--854. Available at: <https://doi.org/10.1038/nmeth.3016>.

Waters, C.M., Roan, E. and Navajas, D. (2012) 'Mechanobiology in Lung
Epithelial Cells: Measurements, Perturbations, and Responses',
*Comprehensive Physiology*, 2(1), pp. 1--29. Available at:
<https://doi.org/10.1002/cphy.c100090>.

Wen, Q. and Janmey, P.A. (2011) 'Polymer physics of the cytoskeleton',
*Current Opinion in Solid State and Materials Science*, 15(5), pp.
177--182. Available at: <https://doi.org/10.1016/j.cossms.2011.05.002>.

Wyatt, T.P.J. *et al.* (2015) 'Emergence of homeostatic epithelial
packing and stress dissipation through divisions oriented along the long
cell axis', *Proceedings of the National Academy of Sciences*, 112(18),
pp. 5726--5731. Available at: <https://doi.org/10.1073/pnas.1420585112>.

Wyatt, T.P.J. *et al.* (2020) 'Actomyosin controls planarity and folding
of epithelia in response to compression', *Nature Materials*, 19(1), pp.
109--117. Available at: <https://doi.org/10.1038/s41563-019-0461-x>.

Xi, W. *et al.* (2018) 'Material approaches to active tissue mechanics',
*Nature Reviews Materials*, 4(1), pp. 23--44. Available at:
<https://doi.org/10.1038/s41578-018-0066-z>.

Yeung, T. *et al.* (2005) 'Effects of substrate stiffness on cell
morphology, cytoskeletal structure, and adhesion', *Cell Motility*,
60(1), pp. 24--34. Available at: <https://doi.org/10.1002/cm.20041>.

Yevick, H.G. *et al.* (2019) 'Structural Redundancy in Supracellular
Actomyosin Networks Enables Robust Tissue Folding', *Developmental
Cell*, 50(5), pp. 586-598.e3. Available at:
<https://doi.org/10.1016/j.devcel.2019.06.015>.

Yu, J.C. and Fernandez-Gonzalez, R. (2016) 'Local mechanical forces
promote polarized junctional assembly and axis elongation in
Drosophila', *eLife*. Edited by J.B. Wallingford, 5, p. e10757.
Available at: <https://doi.org/10.7554/eLife.10757>.

Zampieri, F., Coen, M. and Gabbiani, G. (2014) 'The prehistory of the
cytoskeleton concept', *Cytoskeleton*, 71(8), pp. 464--471. Available
at: <https://doi.org/10.1002/cm.21177>.

[^1]: Ruysch is referred to as a "Artist of death" because of his famous
    anatomical collection. He was the first to use arterial embalming,
    which allowed for visualizing and dissecting smallest arteries. He
    also was part of the macabre practice of public dissections.
    (halley2019)

[^2]: Finding a fundamental unit of living entities comes from the
    philosophy of Gottfried W. Leibniz. It was based on the idea of
    "monad". Thanks to progress in microscopy and philosophy,
    naturalists were able to put together ideas for cells, fibres, and
    even cytoskeleton! (zampieri2014)

[^3]: The famous epigram was coined by François-Vincent Raspail. Virchow
    is regarded as influential biomedical scientist of 19^th^ century,
    but more interesting part is as a radical who took part in the March
    revolution of 1848. He was one of the first to advocate for the
    social origins of illness (wright2012, brown2006).

[^4]: Louis Sullivan is credited with this maxim, but Sullivan's protégé
    Frank Lloyd Wright, designer of New York City's Guggenheim Museum
    said "...that has been misunderstood. Form and function should be
    one, joined in a spiritual union." (Guggenheim2022)

[^5]: Thompson was a polymath, interested in Greek classics to anatomy.
    The work has been influenced by Goethe's structuralism and the
    functionalism of Bertrand Russell. At that time, the dominant
    explanation in biology was "Darwinism." To the extent that the ideas
    of fitness and natural selection would filter in every discipline.
    Thompson believed in physics rooted in classical mechanics.

[^6]: consider *Argyropelecus olfersii* fish mapped onto a cartesian
    coordinate system can be transformed into *Sternoptyx diaphana* fish
    by shear transformation of the grid. This theory of transformation
    has demonstrated its relevance in a new field of geometric
    morphometrics (abzhanov2017).

[^7]: Funnily, He criticized the zoologists and morphologists of the
    time of assigning shapes to psychical instinct of the organism or
    some divine interference for creating the perfect shapes: "He finds
    a simple geometric construction, for instance in the honeycomb
    structure, he would fain refer it to psychical instinct or design
    rather than in the operation of physical forces. \... When he sees
    in snail, or nautilus, or tiny foraminiferal or radiolarian shell a
    close approach to sphere or spiral, he is prone of old habit to
    believe that after all it is something more than a spiral or a
    sphere, and that in this \"something more\" there lies what neither
    mathematics nor physics can explain."

    He was also strong critic of the teleology, where the form can be
    explained because of its function. The intestine has large surface
    area because of its absorption function, or in evolution wolf has
    sharp teeth because of wolf's dietary requirements. Even today in it
    is challenging to abstract oneself from teleology. Thompson has a
    special affinity to the physical explanation by saying,'\...to seek
    not for ends but for antecedents is the way of the physicists, who
    finds causes in what he has learned to recognize as fundamental
    properties, or inseparable concomitants, or unchanging laws, of
    matter and of energy."

[^8]: While, in the introduction of the D'Arcy Thompson's Growth and
    Form we can see that he is not completely able be free of vitalism.
    Especially when comparing dead with alive humans.

[^9]: A fantastic commentary of state of engineered living systems
    research. Matthew Good talks about biologist perspective of building
    cells from interacting molecules and the complexity it entails.
    Xavier Trepat applies the same philosophy for building tissues at
    mesoscale and gives the analogy for the traffic jams.

[^10]: "Mechanical instabilities have provided a unique approach to
    imbue "material intelligence" into soft machines without requiring
    the addition of rigid components. For example, binary actuators
    relying on mechanical instabilities can recreate logic modules and
    reproduce valving functionality using entirely soft elements."
    (pal2021)

[^11]: I cannot recommend enough the chapter "the forms of cell". He
    states "Many forms are capable of realisation under surface-tension,
    ... The subject is a very general one; it is, in its essence, more
    mathematical than physical; it is part of the mathematics of
    surfaces, and only comes into relation with surface-tension because
    this physical phenomenon illustrates and exemplifies, in a concrete
    way, the simple and symmetrical conditions with which the
    mathematical theory is capable of dealing."
