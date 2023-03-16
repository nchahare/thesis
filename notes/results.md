Epithelial sheets form specialized 3D structures suited to their
physiological roles, such as branched alveoli in the lungs, tubes in the
kidney, and villi in the intestine. To generate and maintain these
structures, epithelia must undergo complex 3D deformations across length
and time scales. How epithelial shape arises from active stresses,
viscoelasticity, and luminal pressure remains poorly understood. To
address this question, we developed a microfluidic chip and a
computational framework to engineer 3D epithelial tissues with
controlled shape and pressure. In the setup, an epithelial monolayer is
grown on a porous surface with circular low adhesion zones. On applying
hydrostatic pressure, the monolayer delaminates into a spherical cap
from the circular zone. This simple shape allows us to calculate
epithelial tension using Laplace's law. Through this approach, we
subject the monolayer to a range of lumen pressures at different rates
and hence probe the relation between strain and tension in different
regimes while computationally tracking actin dynamics and their
mechanical effect at the tissue scale. Slow pressure changes relative to
the actin dynamics allow the tissue to accommodate large strain
variations. However, under sudden pressure reductions, the tissue
develops buckling patterns and folds with different degrees of
symmetry-breaking to store excess tissue area. These insights allow us
to pattern epithelial folds through rationally directed buckling. Our
study establishes a new approach for engineering epithelial
morphogenetic events.

*Keywords*: epithelial monolayers, actomyosin cytoskeleton,
morphogenesis, mechanobiology, microfluidics

# Introduction and motivation

The central focus of this thesis is the epithelial tissue monolayer.
From the perspective of a mechanical engineer, these monolayers are
endlessly fascinating. They are remarkable in their ability to change
shape, self-heal, and continuously deform or jam as needed (Xi et al.
2018). They represent the simplest system for gaining a physical
understanding of biological morphogenesis, as epithelia can be found
everywhere in the body, covering the skin and lining various cavities
and organs. The shapes of epithelial monolayers can range from simple
spherical blastocysts to highly branched and folded lungs, and they are
formed and maintained through constant adaptation and renewal. This
thesis aims to explore the physical principles behind epithelial shape
by combining theoretical and experimental approaches in the study of
simple epithelial monolayers.

The chapters in this part serve as a comprehensive overview of all the
key topics related to my PhD research. They begin with a brief
introduction to epithelial tissues and their constituent parts, followed
by a discussion on the role of mechanics in morphogenesis and various
modeling approaches. This part concludes with a review of the growing
field of \"bottom-up\" morphogenesis, where researchers are building
biological systems from scratch.

## Epithelial Layers

### Introduction

[]{#fig_1_1 .anchor}![The Anatomy Lesson of Dr. Frederik Ruysch, 1670 by
Adriaen Backer. (Adriaen Backer Wikipedia
1670)](media/image1.png){width="5.916526684164479in"
height="4.0584306649168855in"}

**The Anatomy Lesson of Dr. Frederik Ruysch**, 1670 by Adriaen Backer.
(Adriaen Backer Wikipedia 1670)

The term "epithelia" was first introduced by Dutch botanist Frederick
Ruysch in the early 18th century (see fig [1.1](#fig_1_1)). He used it
to describe the tissue he observed while dissecting the lips of a
cadaver, and the word is derived from Greek roots "epi," meaning top,
and "thele," meaning nipple. [^1] A few decades later, Swiss scientist
Albrecht von Haller began using the term "epithelium/epithelia" to
describe the fibers of the body, following the old Renaissance theory
that the body was made of fibers, which were believed to be a
fundamental building block of living things. [^2] It was thought that
these fibers and tissues arranged in different arrays gave rise to
biological structures (MacCord 2012; Zampieri, Coen, and Gabbiani 2014).
This theory was not far off, as epithelial tissues make up more than 60%
of the cells in a vertebrate's body and are found ubiquitously, covering
the organs both inside and out (Alberts 2015).

Epithelial cells are polarized, i.e., their apical side (typically
facing the lumen of the organ), which differs in shape and composition
from the basolateral side (see fig [\[fig_1\_2\]](#fig_1_2)). Its polar
organization is reflected in the vectorial functions like creating and
maintaining concentration gradients between separated compartments
(Marchiando, Graham, and Turner 2010). Typical examples of these are
transporting epithelia such as those of the renal tubule, absorptive
epithelia of the intestine, and secretory epithelial cells like
hepatocytes (Alberts 2015). In addition, polarized epithelia guide the
developmental process by determining the fate of cells leading to
symmetry-breaking events in the embryo (Kim, Korotkevich, and Hiiragi
2018).

### Key components

The function of epithelia primarily depends on the tissue's structure
and the surrounding microenvironment. It can be divided into three
aspects: cell structure, microenvironment, and cell-matrix interactions.

#### Cell structure

The cell cytoskeleton plays a crucial role in maintaining cell shape and
supporting vital functions such as cell division and migration (Alberts
2015). The Eukaryotic cell cytoskeleton is composed primarily of
filamentous proteins, including three main types of filaments that
differ in size and protein composition: microtubules, actin filaments,
and intermediate filaments (see fig [1.2](#fig_1_3b)). Microtubules,
with a diameter of approximately 25 nm, are the largest and made of the
protein tubulin. Actin filaments, with a diameter of only 6 nm, are the
smallest. Intermediate filaments, with a diameter of around 10 nm, are
composed of several different subunit proteins and have a diameter
intermediate between the other two types (Mofrad 2009). All three
filament types dynamically respond to signals from the microenvironment
and cell networks.

Mechanically, actin filaments have higher extensional stiffness than
microtubules but break at lower extensions. Intermediate filaments have
intermediate extensional stiffness and can sustain larger extensions
while showing a nonlinear stiffening response (Wen and Janmey 2011).
Differences in strength and stability arise from the properties of
individual subunits. The persistence length can range from $1\mu m$ for
intermediate filaments to $1mm$ for microtubules (Fletcher and Mullins
2010). Actin filaments, most relevant to this thesis, have a persistence
length of a few microns.

The assembly and disassembly of these filaments are dictated by the
dynamics of their macromolecular components and accompanying proteins.
The combination of actin filaments and myosin motors forms the
actomyosin cortex, which is essential in producing intra- and
intercellular forces. In an epithelial tissue, the actomyosin cortex and
intercellular junctions make cell-to-cell contacts stronger and provide
tissue integrity (Braga 2016) (see fig [1.3](#fig_1_3)). A good example
of these tissue-level structures can be observed in wound healing
assays, where cells surrounding the wound create a ring of actin to
close it (Brugués et al. 2014). In Chapter 3, we will delve into the
actomyosin network in more detail.

[]{#fig_1_3b .anchor}![Mechanics of cytoskeletal filaments: Schematic
and sizes of actin filaments, intermediate filaments and microtubules;
along with the strain response to shear stress. Adapted from (Leggett et
al. 2021)](media/image2.png){width="5.305508530183727in"
height="2.242069116360455in"}

***Mechanics of cytoskeletal filaments**: Schematic and sizes of actin
filaments, intermediate filaments and microtubules; along with the
strain response to shear stress. Adapted from (Leggett et al. 2021)*

Multiple membrane molecules can facilitate cell adhesion, including
cadherins. Cadherins are a crucial component for epithelial cell
cohesion and the formation of adherens junctions, which transmit forces
between cells. This key factor is involved in the mechanical regulation
of cell division and tissue rearrangement during development and
homeostasis (Godard and Heisenberg 2019; Mertz et al. 2013). Desmosomes,
another type of intercellular junction, are coupled with intermediate
filaments and provide mechanical resilience to cell layers (Hatzfeld,
Keil, and Magin 2017; Latorre et al. 2018). Tight junctions serve as a
barrier and regulate the active transport of ions across epithelial
layers, playing an important role in controlling fluid pressure in
tissues (Marchiando, Graham, and Turner 2010; Chii J. Chan and Hiiragi
2020).

[]{#fig_1_3 .anchor}![Intercellular forces through actomyosin cables and
cadherins: Schematic showing mechanical connections between adhesions
and tissue force transmission with actomyosin cytoskeleton and adhesion
proteins. Adapted from (Ladoux and Mège
2017)](media/image3.png){width="6.125in" height="1.394076990376203in"}

**Intercellular forces through actomyosin cables and cadherins**:
Schematic showing mechanical connections between adhesions and tissue
force transmission with actomyosin cytoskeleton and adhesion proteins.
*Adapted from (Ladoux and Mège 2017)*

#### Microenvironment

The extracellular matrix (ECM) is the substrate or cell environment to
which cells adhere. It is also referred to as the matrix, mesenchyme, or
cellular microenvironment. The ECM serves many functions. It endows
tissues with strength, thereby maintaining their shape. Additionally, it
serves as a biologically active scaffolding that allows cells to migrate
or adhere. The ECM also plays a role in regulating the phenotype of
cells. It provides an aqueous environment that facilitates the diffusion
of nutrients, ions, hormones, and metabolites between the cell and the
capillary network (Alberts 2015).

Moreover, the ECM is subjected to mechanical forces such as blood flow
in endothelia, air flow in respiratory epithelia, or hydrostatic
pressure in the mammary gland and bladder (Waters, Roan, and Navajas
2012; Walma and Yamada 2020). It has been shown that the ECM regulates
cell shape, orientation, movement, and overall function in response to
biophysical forces (Alberts 2015).

The ECM is a fibrous network of proteins, consisting of collagen,
elastin, and proteoglycans as its primary structural components.
Collagen is one of the most abundant proteins in the body, while elastin
is the most elastic and chemically stable protein. Proteoglycans can
sequester significant water as well as growth factors and proteases. The
water content of the ECM allows it to deform as a poroelastic material,
absorbing water upon stretching and releasing it under compression,
causing a hydraulic fracture effect (Casares et al. 2015). The collagen
network can also remodel under the influence of cells and mechanical
forces (Humphrey, Dufresne, and Schwartz 2014).

Most ECM components undergo continuous turnover, some quickly and some
slowly. For example, the half-life of collagen in the periodontal
ligament is a few days, whereas that in the vasculature may be several
months (Humphrey, Dufresne, and Schwartz 2014). In response to altered
physical stimuli, disease, or injury, the rates of collagen synthesis
and degradation can increase many times, allowing for a rapid response.

#### Cell-Matrix interaction

[]{#fig_1_4 .anchor}![Cell-matrix interaction with respect to matrix
stiffness and cell density: In higher tension condition, the nucleus is
deformed triggering mechanotransduction and causing alterations in
cytoskeleton and tractions. Adapted from (Xi et al.
2018)](media/image4.png){width="5.779632545931759in"
height="1.6944903762029746in"}

**Cell-matrix interaction with respect to matrix stiffness and cell
density**: In higher tension condition, the nucleus is deformed
triggering mechanotransduction and causing alterations in cytoskeleton
and tractions. *Adapted from (Xi et al. 2018)*

The cells and the extracellular matrix (ECM) are in a dynamic
relationship, constantly exchanging information and influencing each
other. The cells sense the biophysical cues in the ECM through sensors
such as integrins and focal adhesion complexes, which are responsible
for cell-substrate adhesion (Kechagia, Ivaska, and Roca-Cusachs 2019)
(see fig [1.4](#fig_1_4)). These adhesions allow cells to respond to
various stimuli such as matrix stiffness, ligand density, and
chemotactic gradients (Fortunato and Sunyer 2022). It has also been
shown that cells can respond to the viscoelasticity of the matrix
(Elosegui-Artola et al. 2022).

In addition to sensing the ECM, cells also contribute to its composition
by secreting ECM components or remodeling the substrate (Malandrino et
al. 2018). This interplay between the cells and ECM can impact the
tissue behavior fundamentally, as the connections between focal
adhesions and the nucleus can affect the expression of transcriptional
factors (Venturini et al. 2020; Lomakin et al. 2020). The precise
control of cell-cell and cell-substrate interactions enables cells to
transform into intricate shapes, such as curved forms in cell sheets
(Schamberger et al. 2022).

### Role in disease and development

Maintaining epithelial integrity and homeostasis is crucial for
survival, and mechanisms have evolved to ensure these processes are
sustained during growth and in response to damage. Epithelial cells have
one of the fastest turnover rates in the body, with the entire gut cell
lining turning over in 5--7 days (Barker 2014). This constant cell
division and death pose a risk for tumor formation; it is know that 90%
of cancers emerging in simple epithelia (Torras et al. 2018; Eisenhoffer
and Rosenblatt 2013). Additionally, the high rate of cell turnover can
disrupt the barrier function, as gaps should not emerge around dividing
or dying cells.

If the fluid compartmentalization goes awry, it can have profound
implications for epithelial and stromal homeostasis, fluid and
electrolyte balance, and the development of inflammatory states. Several
bacterial toxins are known to target junctions, causing changes in the
tight junction protein ZO1, which compromises the barrier function and
leads to pathologies such as diarrhea and colitis (Fasano et al. 1991).
In cancer, the compromised ZO1 barrier is essential to allow metastatic
cells to break into and out of blood vessels. The leaky barrier also
enables a growing epithelial tumor to access luminal fluids as an
additional source of nutrients (Mullin et al. 2005).

Furthermore, epithelia participate in physiological events such as
epithelial--mesenchymal transition (EMT), which is a developmental
process where epithelial cells gradually transform into mesenchymal-like
cells by losing their epithelial functionality. EMT plays a vital role
in normal biological functions such as repair and differentiation, as
well as abnormal pathological activity such as organ fibrosis and
promoting carcinoma progression (Alberts 2015). EMT endows cells with
stem cell properties, enabling cell migration to distant organs and
subsequent differentiation into multiple cell types during development
and the initiation of metastasis (Thiery et al. 2009).

Epithelia undergo drastic shape changes with deformation and
reorganization from the embryonic to the adult stage. It's not
surprising that any malfunction in this process can lead to damage and
disorder, resulting in congenital malformations, which are a major cause
of infant mortality worldwide (Clarke and Martin 2021). Additionally,
epithelial dysfunction is a precursor to diseases such as chronic
obstructive pulmonary disease, asthma, cystic fibrosis, and pulmonary
fibrosis (Carlier, de Fays, and Pilette 2021).

### Forms of epithelia

The structure and arrangement of epithelial cells are crucial for
maintaining the integrity and homeostasis of tissues and organs (see fig
[1.5](#fig_1_5)). Simple epithelia are single-cell layers where all
cells are in contact with the underlying basal lamina and have a free
surface on the apical side. The shape of the cells can vary, ranging
from flat to cuboidal to columnar. Stratified epithelia, on the other
hand, have two or more layers of cells. Additionally, there are
pseudostratified epithelia, which appear to be stratified, but are
monolayers where the cell nuclei are positioned in a manner that gives
the appearance of a stratified epithelium.

The classification of epithelia was first established in the XIXth
century based on their structure and physiological characteristics. Germ
layer theory, developed by embryologists, further expanded the
epithelial nomenclature (MacCord 2012). During early embryogenesis,
three layers emerge: endoderm, mesoderm, and ectoderm. The ectoderm
forms the epithelia lining the skin, mouth, and nervous system, while
the endoderm gives rise to the digestive tract, respiratory system, and
liver. The mesoderm, in turn, develops the endothelia covering much of
the circulatory and lymphatic systems.

It is important to note that not all tissues classified as epithelia,
mentioned in this thesis, are purely composed of epithelial cells. They
may be a mixture of different cell types that have epithelial-like
characteristics. The focus of this thesis is on packed cell monolayers,
which can form and self-organize into various 3D shapes, ranging from
simple spheres to complex branched tubules. The thesis will explore the
role of mechanics in epithelial morphogenesis.

[]{#fig_1_5 .anchor}![Forms of epithelial tissues: Simple squamous,
cuboidal, columnar epithelia and pseudostratified epithelia. Adapted
from ("Animal Tissues. Covering Epithelium. Atlas of Plant and Animal
Histology." n.d.)](media/image5.png){width="6.125in"
height="1.4358300524934384in"}

**Forms of epithelial tissues**: Simple squamous, cuboidal, columnar
epithelia and pseudostratified epithelia. *Adapted from ("Animal
Tissues. Covering Epithelium. Atlas of Plant and Animal Histology."
n.d.)*

## The mechanical basis of Morphogenesis

### The complexity of the morphogenesis

Epithelial cells play a crucial role in the formation of transient
structures during embryonic development, such as the neural tube,
somites, and precardiac epithelium, which serve as the precursor for the
development of complex organs. During this process, different types of
epithelia acquire distinct morphological forms and perform specific
functions, including branched lungs, looped gut, kidney tubules, thyroid
follicles, and sinusoids in the liver. The regulation of epithelial
morphogenesis is a complex and hierarchical process that involves
coordinated events at multiple spatial and temporal scales (Trepat and
Sahai 2018).

Some processes appear to be happening fast at the local level, such as
cell shape changes through apical constrictions, which lead to global
changes, such as the formation of a ventral furrow in a Drosophila
embryo (Martin, Kaschube, and Wieschaus 2009). At the same time,
chemical signaling events that activate these processes are slow and
occur at a global level. The same complexity can be seen in *in vitro*
systems, where a cluster of dissociated stem cells can assemble into an
organoid or gastruloid and undergo global folds in response to
appropriate culture conditions (Collinet and Lecuit 2021).

The underlying mechanisms of epithelial morphogenesis are intricate and
involve multiple factors, including genes responding to morphogen
gradients, molecular machinery involved in apical constriction, and
mechanical stresses that cause tissue-scale deformations. To fully
understand the phenomenon of epithelial morphogenesis, it is essential
to study these processes in detail, at multiple levels of complexity
(Schöck and Perrimon 2002; Lecuit, Lenne, and Munro 2011).

Rudolf Virchow's third tenet of the cell theory states that "omnis
cellula e cellula," meaning "all cells come from cells" (Virchow et al.
1860). [^3] Although all tissues originate from cells that contain
essentially the same genetic information, each tissue has a distinct
architecture and function. This raises several questions, such as: what
makes cells different from each other? Are differences due to genes,
environmental factors, or both? What drives shape changes in tissue
morphogenesis? Over the last two centuries, the field of developmental
biology has addressed many of these questions, but it has also raised
new issues and left others unanswered.

Until last decade, the focus of the field had been on tracking and
mapping patterns of cell movements to patterns of gene or protein
expression (Gorfinkiel and Martinez Arias 2021). While these studies are
influential and important for understanding morphogenetic patterns, they
fall short in explaining how cells and tissues are physically shaped
(Veenvliet et al. 2021; Odell et al. 1981). This is because the physical
understanding of tissues has been limited to kinematic descriptions,
which only describe tissue deformation or cell motion. However, we know
that cells and tissues actively drive shape changes and movements
through the generation of mechanical forces (Lecuit, Lenne, and Munro
2011). Thus, to have an integrated understanding of morphogenesis, we
must consider the role of forces and mechanics.

### On growth and form

Throughout history, the form of both animate and inanimate objects has
been closely linked to their intended function. In fact, the XXth
century architecture principle "form follows function" highlights the
idea that the organization of a structure should be based on its
intended purpose. Similarly, in developmental biology, self-assembling
systems such as intestinal organoids, cancer spheroids, and gastruloids
are perfect examples of this principle in action, as each structure
emerges from a set of cells in a suitable environment, adapting to
perform a specific biological function (Nikolce Gjorevski et al. 2016;
Ishiguro et al. 2017; Morizane and Bonventre 2017; Vianello and Lutolf
2019).

However, the opposite design principle appears to be at work in numerous
*in vitro* experiments that involve a controlled cellular environment.
In such experiments, geometric constraints appear to drive biological
function (Xi et al. 2018). For instance, seeding stem cells in a
bio-printed three-dimensional geometry of the gastrointestinal tract led
to the production of functional tissues with physiological
characteristics of the intestine. The curvature of the structure can
even control the formation of villus-like structures (Brassard et al.
2021).

[]{#fig_2_1 .anchor}![Multiscale imaging and tracking of embryo cell
dynamics: Top panels show in toto imaging of germlayer specification;
red is mesendoderm, blue is epiblast, and yellow is endoderm. Bottom
panel shows data analysis of long term pan embryo cell dynamics (Shah et
al. 2019)](media/image6.png){width="6.125in"
height="3.1152898075240594in"}

**Multiscale imaging and tracking of embryo cell dynamics**: Top panels
show in toto imaging of germlayer specification; red is mesendoderm,
blue is epiblast, and yellow is endoderm. Bottom panel shows data
analysis of long term pan embryo cell dynamics (Shah et al. 2019)

In a way, assembly of biological systems treads the line between
self-organization and programmed material. Advanced microscopy
techniques have allowed us to witness the intricacies of developmental
processes with unprecedented clarity (see fig [2.1](#fig_2_1)). We can
now observe cells and their motion throughout the morphogenetic process,
from the formation of a spherical embryo to the creation of a complete
organism (Shah et al. 2019). Cells undergo shape changes and large-scale
flows as they undergo morphogenesis, driven by mechanical forces in
concert with biochemical processes (Labernadie and Trepat 2018; Trepat
and Sahai 2018; Lecuit, Lenne, and Munro 2011). Thus, the dichotomy of
form and function is incomplete without considering the physical laws of
mechanics.

Over a century ago, D'Arcy Wentworth Thompson wrote the influential book
"On Growth and Form" (Thompson 1979), in which he explored the
relationship between geometry, physics, and biology in the context of
morphogenesis. Thompson used examples to show how mathematical
principles can explain biological phenomena, such as his theory of
transformations, which demonstrates how related species can be
represented geometrically (see fig [2.2](#fig_2_1b)). According to
Thompson's daughter, he even used to draw pictures of dogs on rubber
sheets and stretch them to show children how poodles could become
dachshunds ("Are All Fish the Same Shape If You Stretch Them? The
Victorian Tale of On Growth and Form," n.d.). This distortion of shape
represents significant alterations in various forces or rates of growth
throughout the developmental processes of different organisms.

Thompson's approach was highly speculative, but his goal was to identify
general principles behind the diverse forms and patterns found in
biology. He compared growth curves of haddock, trees, and tadpoles, and
found logarithmic spirals in shells, horns, and leaf arrangements. [^4]
Essentially, this book emphasized two points: first, all material forms
of living things---cells, tissues, and organs---must obey the laws of
physics, and second, quantitative measurements are necessary to unravel
the physical principles of biology.

[]{#fig_2_1b .anchor}![D'Arcy Thompson's fishes and his theory of
transformation. (Wolfram 2017; Thompson
1979)](media/image7.png){width="4.462436570428697in"
height="2.5358923884514435in"}

**D'Arcy Thompson's fishes** and his theory of transformation. (Wolfram
2017; Thompson 1979)

Thompson's work continues to inspire researchers even today. Right as I
began my Ph.D., the centenary of the book's publication was being
celebrated in the fields of developmental biology and biophysics (Heer
and Martin 2017; "The 100-Year-Old Challenge to Darwin That Is Still
Making Waves in Research" 2017; "A Ton for Thompson's Tome" 2017). Even
more so by the field of mechanobiology, an interdisciplinary field that
studies the role of biophysical forces in cell and tissue functioning.

### Mechanobiology

The cells within epithelial tissue can be viewed as mathematical systems
that integrate multiple input cues to result in an output behavior.
These inputs can be mechanical or chemical, such as the stretching of
lungs or the presence of morphogen gradients during embryonic
development. The outputs can include cell deformation, migration,
differentiation, or proliferation (Kumar, Placone, and Engler 2017).
Some outputs can even feedback into the system as an input, such as when
cells remodel the matrix (Malandrino et al. 2018). Mechanochemical
switches at the membrane, cell-cell junctions, or cell-matrix adhesions
mediate the sensing of the environment, triggering a biochemical cascade
that leads to a cellular response (Roca-Cusachs, Conte, and Trepat
2017). This interplay between biochemistry and mechanics is known as
mechanotransduction.

During morphogenesis, mechanotransduction occurs at various scales,
ranging from a single cell to complex multicellular tissue. To
understand the role of different variables, experiments at different
scales are necessary. It has been observed that individual cells can
sense their environment and respond by altering their behavior through
mechanical or biochemical processes. Whereas, multicellular systems can
transmit forces and information at a longer length scale, allowing for
emergent characteristics such as collective migrations, oscillations,
rearrangements, and even turbulent flows (Heer and Martin 2017; Lecuit,
Lenne, and Munro 2011; Trepat and Sahai 2018).

An excellent demonstration of the interaction between tissues and their
environment is provided by the phenomenon of durotaxis. Epithelial cells
can detect changes in the stiffness of the extracellular matrix and
migrate towards areas of higher rigidity. This migration towards stiffer
regions has been observed both *in vitro*, where cells in a monolayer
collectively expand and relocate to stiffer areas, and *in vivo*, such
as during the migration of neural crest cells in *Xenopus laevis*
(Sunyer et al. 2016; Shellard and Mayor 2021). It is worth noting that
the migration of neural crest cells themselves generates the durotactic
gradient. In another example, during Drosophila oogenesis, the
disorganized matrix is remodeled by cells to create a polarized matrix
that aligns with the actin bundles in the follicular epithelium. This
alignment is achieved through the coordinated rotation of cells and can
guide the directed motion of cells along the polarized fibers (Haigo and
Bilder 2011; Cetera et al. 2014).

The interplay between individual cells, their neighbors, and exogenous
stimuli makes it difficult to decouple various biophysical aspects of
the environment, such as forces, pressures, matrix stiffness, spatial
confinement, porosity, or viscoelasticity. Direct force measurements in
and out of tissues are also challenging. To address these challenges,
researchers from various disciplines have attempted to recreate
experimental systems with precise control over the biochemical and
mechanical environments of cells (Xi et al. 2018). This has been made
possible through continuous technological advancements in fluorescent
probes, imaging, microfabrication, and force measurements (Roca-Cusachs,
Conte, and Trepat 2017). In the following section, I will provide an
overview of relevant techniques and experiments in the field of
mechanobiology.

#### Synthetic substrates

The use of Polyacrylamide and soft PDMS (polydimethylsiloxane) gels has
enabled researchers to investigate mechanical interactions at
cell-substrate adhesion (see fig [2.3](#fig_2_2) A). Simply seeding
cells on hydrogels of different stiffnesses reveals a significant impact
on the actin cytoskeleton, cell shape, and lineage specification (Yeung
et al. 2005; Engler et al. 2006). These substrates, because of their
known elastic response, are also utilized in techniques like traction
force microscopy (TFM) to measure the forces exerted by cells and
tissues on the substrate (A. K. Harris, Wild, and Stopak 1980;
Gómez-González et al. 2020) (see fig [2.3](#fig_2_2) D). TFM studies
have shown that cells and tissues can exert greater forces on stiffer
substrates as a result of the remodeling of the cytoskeleton
(Elosegui-Artola et al. 2016). Higher matrix stiffness has also been
found to induce the translocation of Yes-associated protein (YAP) from
the cytoplasm to the nucleus, which is considered a sensor for
mechanotransduction (Elosegui-Artola et al. 2017). However, increasing
extracellular matrix (ECM) ligand density alone can induce YAP nuclear
translocation without changing substrate stiffness (Stanton, Tong, and
Yang 2019).

#### Geometric control

The shape of cells or tissues on 2D substrates can be controlled using
micropatterned adhesion proteins or microfabricated stencils. Protein
patterning techniques are used to pattern adhesion promoting proteins
and control cell attachment and spreading, while microfabricated
stencils physically confine cells in a particular geometry (see fig
[2.3](#fig_2_2) B C). When cells are confined, they respond by
reorganizing their actin cytoskeleton and focal adhesion complexes to
match the shape imposed on them (Vignaud, Blanchoin, and Théry 2012).
Confined tissues undergo larger-scale rearrangements, leading to the
formation of fascinating topological defects or oscillations (Tlili et
al. 2018; Balasubramaniam et al. 2021; Guillamat et al. 2022). Through
these experiments, we can uncover the mechanisms of force transmission
and regulation of collective cell migration and epithelial growth in two
dimensions (Nelson et al. 2005; Vedula et al. 2012; Deforet et al.
2014).

Embryonic stem cells subjected to 2D confinement have been shown to
differentiate based on the shape and size of the confinement. For
example, a circular monolayer of stem cells can reproduce the tissue
patterning of a 3D gastruloid (Warmflash et al. 2014), and confinement
in a triangular shape can lead to high tension at the vertices and
activate Wnt signaling, promoting differentiation to mesoderm (Muncie et
al. 2020). Moreover, advancements in photopatterning technologies allow
for precise control of multiple proteins on the same substrate (Guyon et
al. 2021; Prahl et al. 2022), enabling the establishment of complex
co-culture systems that mimic *in vivo* events.

Not just 2D shape, epithelial monolayers are also able to respond to
curvature by regulating cell migration, orientation, cell/nucleus size,
and shape (Marín-Llauradó et al. 2022; Schamberger et al. 2022) (see fig
[2.3](#fig_2_2) C). For example, an epithelial monolayer on hemispheres
of elastomers acts as a fluid with increasing curvature (Tang et al.
2022). On a smaller scale, cells attached to corrugated hydrogels show
variations in lamins, chromatin condensation, and cell proliferation
rate in response to curvature (Luciano et al. 2021). Bio-printing of
three-dimensional tissue architectures can also create functional
tissues (Brassard et al. 2021; Breau et al. 2022).

[]{#fig_2_2 .anchor}![Mechanobiological strategies for studying
morphogenesis Adapted from (Vianello and Lutolf
2019)](media/image8.png){width="6.125in" height="5.862053805774278in"}

**Mechanobiological strategies for studying morphogenesis** *Adapted
from (Vianello and Lutolf 2019)*

#### Mechanical control

Living systems have mechanical control in addition to spatial control,
as physical forces emerge from growth, deformation, and remodeling of
the extracellular matrix (ECM) and fluid pressure in closed geometries.
For example, the intestinal epithelia are stretched during peristaltic
movements in the gut and lung alveoli deformations during breathing.
Compression can also guide morphogenetic events that involve tissue
bending and folding, such as the formation of the optic cup, gut villi,
and cortical convolutions in the brain (Okuda et al. 2018; Shyer et al.
2013; Tallinen et al. 2016).

To study tissue behavior under external perturbation, cells and tissues
are probed at the molecular and subcellular scales using techniques such
as atomic force microscopy, magnetic beads, optical tweezers, and
micropipettes (Bao and Suresh 2003) (see fig [2.3](#fig_2_2) E). At a
larger scale, various types of stretching devices, tissue rheometers,
and force plates can be used (Xi et al. 2018). These experiments reveal
that cells exhibit complex viscoelastic behavior at different levels of
deformation and different regions of the cytoskeleton (Mofrad 2009). The
response of tissues to stretching can vary depending on the timescale of
the stretch and the reorganization of cells within the tissue (Guillot
and Lecuit 2013). Rheological experiments also help to uncover the role
of signaling pathways, such as YAP transcription factors, in
mechanosensation (Wagh et al. 2021).

The microfluidic system, also known as "cells on a chip," has emerged as
a valuable tool for investigating cell behavior under controlled
biophysical conditions that mimic *in vivo* conditions (Ingber 2018).
This system allows for the application of stretch or shear forces, as
well as the creation of a controlled microenvironment that mimics the
organ-level cues present in the body. For instance, the surface tension
at the air-liquid interface in the lungs and the fluid flow through the
vasculature, as well as the cyclic mechanical stretch of the
tissue-tissue interface due to breathing, can be replicated using this
approach (Huh et al. 2010).

In the context of developmental biology, the use of microfluidic systems
has allowed for the study of self-organization and embryo functions
under controlled physical conditions. The co-culture of iPSC-derived
motoneurons and brain microvascular endothelial cells in a microfluidic
system has produced the *in vivo*-like maturation of spinal cord neural
tissue, representing a new avenue for exploring the complex interplay
between physical and biological factors in development (Sances et al.
2018; Samal et al. 2019).

As mentioned earlier, the tissue-matrix interaction plays a critical
role in sensing and rapidly transmitting forces (Tambe et al. 2011;
Sunyer et al. 2016; Serra-Picamal et al. 2012). However, in early
embryonic epithelia where little or no ECM is present, stresses
generated by actomyosin contraction of the cells in one tissue are
transmitted over long ranges via intercellular adhesions to other
tissues. Thus, studying a simple free-standing epithelial monolayer is
very appealing in terms of characterizing the mechanical response to
stretch at different time scales.

Only two techniques are available for this: first, Harris and colleagues
created a suspended monolayer by culturing a cell monolayer on a
collagen matrix on two rods, and later removed the matrix using
enzymatic digestion (A. R. Harris et al. 2012). Second, epithelial
domes, where MDCK cells pump ions to form fluid-filled blisters, have
been used (Lever 1979). Recently, my colleagues, Ernest Latorre and
Ariadna Marin-Llaurado, have enhanced control over the curvature, shape,
and size of the domes (Latorre et al. 2018; Marín-Llauradó et al. 2022),
details on this system in the next chapter. These experiments showed
that elasticity measurements of the monolayer were two orders of
magnitude larger than those of individual cellular parts, and the
monolayer could sustain more than 200% strain before the rupture of
cell-cell junctions. The cell cytoskeleton, particularly the actomyosin
network and cadherin junctions, actively remodel during stretching,
while the keratin network reinforces monolayer integrity at higher
strains (Latorre et al. 2018; Duque et al. 2023). With sustained
stretching, the tissue undergoes significant realignment and
rearrangement via division (T. P. J. Wyatt et al. 2015). Experiments on
tissue devoid of the matrix also revealed epithelial actions such as
superelasticity and buckling (Latorre et al. 2018; T. P. J. Wyatt et al.
2020).

#### 3D systems

*In vitro* experiments with 2D or 2.5D cell systems have improved our
understanding of cell mechanics in morphogenesis by allowing us to
measure deformations and forces and control environmental conditions
that are inaccessible *in vivo*. However, to gain a deeper understanding
of cell mechanics, systems closer to the *in vivo* environment must be
probed.

Cell aggregates are a promising *in vitro* system for probing cell
mechanics, where synthetic matrix and mechanical measurement tools can
be used. The response of cell clusters to the matrix, while similar to
planar tissues, is more complex and includes sensitivity to matrix
stiffness, confinement, and ECM concentration, as well as the ability to
undergo 3D shape transformations (see fig [2.3](#fig_2_2) E). Our lab
has demonstrated that cell aggregates perform durotaxis and exhibit
wetting behavior dependent on stiffness (Pérez-González et al. 2019;
Pallarès et al. 2022). Additionally, cell aggregates in suspension
behave like viscous droplets and can be used to measure rheological
properties, such as when squeezed between plates or probed with AFM or a
micropipette (Xi et al. 2018). The viscoelastic properties of cell
aggregates can even be measured by coalescing two aggregates (Oriola et
al. 2022).

In recent years, the use of hydrogel systems for the culturing cell
aggregates has gained significant attention. Hydrogels, such as
polyethylene glycol (PEG), polyacrylamide, collagen, or Matrigel, serve
as a supportive environment for cell growth. Naturally extracted
hydrogels like Matrigel provide a similar architecture to the native
ECM. When embedded into a hydrogel, polarized epithelia tend to form a
spherical structure with a hollow lumen, which can be induced to form
branching morphogenesis by hepatocyte growth factor (Bryant and Mostov
2008).

Cell-driven self-assembly in organoids leads to tissue formation that
mimics organ features, but achieving reproducibility in shape and
composition is often challenging (Nelson, Inman, and Bissell 2008; Hofer
and Lutolf 2021). Synthetic hydrogels with control over ligand
presentation, crosslinking, and degradability have proven useful for
epithelial organoids, allowing for control over cell fate (Nikolce
Gjorevski et al. 2016; N. Gjorevski et al. 2022).

3D gel-based culture systems with spatiotemporal control over the
mechanical properties corresponding to *in vivo*-like functional
structures have also been developed (Torras et al. 2018). Interestingly,
recent publications show tissue transformation from planar to complex
organ-resembling tissue without fine environmental control. For example,
intestinal epithelium mechanically compartmentalizes itself, and 2D stem
cells transform into a 3D neural tube (Pérez-González et al. 2021;
Karzbrun et al. 2021).

In developing embryos, both embryonic and extraembryonic fluids generate
frictional and tensional stresses when flowing, or hydrostatic pressures
when confined within spaces (Vianello and Lutolf 2019; Chii J. Chan and
Hiiragi 2020). The challenge of measuring these forces has led to the
use of various techniques, including micropipette aspiration.
Micropipette experiments, where a needle is inserted into the embryo to
control pressure, have revealed that the internal hydrostatic pressure
determines the embryonic size and dictates cell fate allocation (Chii
Jou Chan et al. 2019) (see fig [2.3](#fig_2_2) E). As a fluid-filled
structure, the hydrostatic pressure inside the embryo corresponds to
tension in its surfaces, and changes in luminal volumes are sensed by
cells through increased cortical tension, inducing changes in cell shape
and cytoskeleton organization (Chii Jou Chan et al. 2019; Choudhury et
al. 2022). Micropipette aspiration has also been effective in measuring
the surface tension of individual cells or whole blastomeres (Dumortier
et al. 2019), thus providing insight into the role of the actin cortex
in regulating preimplantation embryonic contractility (Özgüç et al.
2022; Firmin et al. 2022).

The measurement of forces within embryos has also been approached
through the insertion of deformable probes, such as hydrogels, oil, or
magnetic droplets (Dolega et al. 2017; Campàs et al. 2014; Serwane et
al. 2017). The shape changes of these probes allow for measurement of
local forces and osmotic pressures (Mongera et al. 2023).

In addition to embryos, explant systems have been utilized to study
organogenesis in the brain, gut, and lungs. Lung explant research has
been particularly useful in understanding different aspects of shape
formation, which occurs under the influence of pressure and growth
factors. The explant system allows for direct control over the chemical
and mechanical environment at specific stages of development. Work with
mouse airway epithelium has shown that pressure and matrix stiffness
impact the number of lung branches (Palmer et al. 2021; Varner et al.
2015; Nelson et al. 2017).

Other tools such as optical tweezers, laser ablation, and optogenetic
excitations have been used at different levels to probe the mechanics of
development (Lecuit, Lenne, and Munro 2011; Gómez-González et al. 2020).
However, independent control over multiple factors remains difficult and
force measurement remains indirect.

In conclusion, epithelial tissues are highly sensitive to various
biophysical forces and constantly undergo remodeling at different scales
and timeframes. There are multiple techniques available to manipulate
and study these tissues, from single cells to embryos, with controlled
forces and deformation. Due to its dynamic behavior, epithelial tissue
can be considered an active material. The focus of this thesis is to
develop a system that can control and measure physical forces to
understand epithelial behavior as an active material. In the following
chapter, we will delve into the molecular machinery responsible for
driving these active tissues.

## Active tissue mechanics

### Force generation with actin

In the field of morphogenesis, cells are central to the formation of
specific structures through changes in their shape. Early embryologists
posited the existence of a mysterious external vital force that guides
the morphogenesis of individual cells in tissues (Thompson 1979).
However, as research progressed, particularly experiments by Wilhelm His
and Wilhelm Roux, it became clear that the physical forces generated
within the cell itself (Clarke and Martin 2021). In the present day, we
now understand, what was unknowable in the XIXth century, that the
machinery responsible for generating these physical forces is the actin
cytoskeleton.

Specifically, the actomyosin cortex forms a mesh containing actin
filaments and myosin motors just beneath the plasma membrane of a cell
(Alberts 2015). This mesh is organized into various higher-order arrays
capable of dynamic remodeling, giving rise to the complex shapes and
structures we observe in the world around us. We can understand the
actomyosin cortex step by step, starting from its basic organization of
single actin filaments to higher-order supracellular actomyosin cables.

[]{#fig_3_1 .anchor}![Actin and Myosin: (A) Electron micrograph of Actin
filament with zoomed in images of barbed and pointed end. (B) Same for
Myosin II minifilament with clearly visible two globular heads and a
long tail. (C-D) Actin network can apply pushing force through
polymerization of single filaments or network expansion. (E,F) While
myosin activity would lead to contraction of the networks. Adapted from
A-B (Alberts 2015) and C-F (Clarke and Martin 2021)
](media/image9.png){width="6.125in" height="3.812584208223972in"}

**Actin and Myosin**: (A) Electron micrograph of Actin filament with
zoomed in images of barbed and pointed end. (B) Same for Myosin II
minifilament with clearly visible two globular heads and a long tail.
(C-D) Actin network can apply pushing force through polymerization of
single filaments or network expansion. (E,F) While myosin activity would
lead to contraction of the networks. *Adapted from A-B (Alberts 2015)
and C-F (Clarke and Martin 2021)*

#### Actin filaments

The actin filaments are helical polymers composed of G-actin proteins
(see fig [3.1](#fig_3_1) A). The asymmetrical nature of these proteins
leads to the development of two distinct ends, referred to as the barbed
and pointed ends, that can be differentiated based on their appearance
in electron micrographs. The actin filaments are known for their dynamic
assembly and disassembly processes, where the distinct ends have
different rates of kinetics. This results in growth in the direction of
the barbed end, with the length of the filament can be maintained by a
constant flux of subunits from the pool of monomers in the cell and
nucleotide hydrolysis. This process is referred to as *treadmilling*
(see fig [3.2](#fig_3_2) A). However, if one end of the filament is
capped, it will continue to grow and apply a pushing force in the
outward direction.

#### Actin networks

[]{#fig_3_2 .anchor}![Forms of actin networks: (A) Actin treadmilling:
where highlighted actins move from positive end to negative end as the
filament polymerizes and depolymerizes from both ends. (C) In an
adherent cells, there are many different kinds of actin structures from
contractile network to gel-like cortex. (B,D,E,F) Actin structures can
be thought as meshwork of actin filaments (red) with
crosslinkers(green). Different crosslinkers produce distinct form of
actin network. Adapted from (Alberts 2015)
](media/image10.png){width="6.125in" height="4.146504811898513in"}

**Forms of actin networks**: (A) Actin treadmilling: where highlighted
actins move from positive end to negative end as the filament
polymerizes and depolymerizes from both ends. (C) In an adherent cells,
there are many different kinds of actin structures from contractile
network to gel-like cortex. (B,D,E,F) Actin structures can be thought as
meshwork of actin filaments (red) with crosslinkers(green). Different
crosslinkers produce distinct form of actin network. *Adapted from
(Alberts 2015)*

Actin filaments can also form branched networks, facilitated by the
presence of nucleation sites on the filament and proteins containing
actin-binding motifs. The actin nucleation can be catalyzed by two
primary factors, the ARP 2/3 complex or formins. The ARP 2/3 complex
creates a pointed end in the center of a filament, leading to the
formation of a new branch from that site. This results in the formation
of a tree-like network of branches, capable of generating sufficient
pushing forces to move a part of the cell membrane (see fig
[3.2](#fig_3_2) E,F). The formins, in conjunction with profilin, aid in
the growth of the filaments, with profilin serving as a staging area for
the rapid addition of monomers to the filament. These structures can
take the form of dendritic actin networks that enable membrane
protrusion at lamellipodia or spike-like projections of the plasma
membrane that allow a cell to explore its environment (see fig
[3.2](#fig_3_2) C). The pushing forces generated at the molecular level
are of the order of 1 piconewton.

#### Actin cortex

The actin filaments can also form tight or loose bundles, facilitated by
crosslinking proteins. Fimbrins enable multiple actin filaments to
arrange in parallel, resulting in closely packed bundles that exclude
myosin from connecting to the filaments. On the other hand,
$\alpha$-actinin crosslinks actin filaments with opposite polarity into
a loose bundle, allowing myosin to bind and create contractile bundles
(see fig [3.2](#fig_3_2) B). Myosin II oligomerizes into a bipolar short
filament that can connect multiple actin filaments and move across them,
resulting in a pulling effect (see fig [3.1](#fig_3_1) B). This movement
is driven by ATP hydrolysis making contracting an active process. The
loose bundle forms the gel-like network in the cell cortex. Other actin
crosslinking proteins can result in different structures. Filamin
creates a loose and viscous gel that is essential for migration, while
spectrin creates a strong and flexible web-like network of short actin
filaments that allows cells to reversibly deform (see fig
[3.2](#fig_3_2) D). The actomyosin bundles in the cortex can generate
two orders of magnitude more force than a single filament (Clarke and
Martin 2021).

### Actin structures at a larger scale

During epithelial morphogenesis, individual cells can undergo shape
changes by modifying their contractility or actin turnover, resulting in
the development of tissue curvature. As mentioned previously, epithelial
cells exhibit apicobasal polarity, which results in a non-uniform
distribution of the actin cytoskeleton that influences cell shape and
tissue architecture.

The geometry of columnar or wedge-like cells in a monolayer determines
the specific ways in which they can be organized (Gómez-Gálvez et al.
2021). Columnar cells, when arranged together, produce a flat tissue,
while wedge-shaped cells with a narrow top result in convex curvature
(see fig [3.4](#fig_3_4) A ). Conversely, concave curvature with a
narrow bottom can also be created. By observing the actin cytoskeleton,
we can determine the specific mechanisms of tissue shaping (see fig
[3.4](#fig_3_4) B). For example, apical constriction with concentrated
actin cortex on the apical surface is involved in multiple convexly
curved tissues, such as the invagination of the intestinal crypt, the
Drosophila mesoderm, and the vertebrate lens placode (Pérez-González et
al. 2021; Lecuit, Lenne, and Munro 2011; Houssin et al. 2020).

[]{#fig_3_3 .anchor}![Actin organization at different scales:(A)
Electron micrograph of actin cortex of mitotic Hela cells (Kelkar,
Bohec, and Charras 2020). (B) Different forms of actin organization in
circular fibroblast cell (Jalal et al. 2019) Scale= 10\\mu m. (C)
Supracellular actin ring during wound closure (Brugués et al. 2014)
Scale=20 \\mu m. (D) Dorsal closure of amnioserosa with actin network
(Ducuing and Vincent 2016) Scale= 10 \\mu m. (E) Supra-cellular
organization of actin for cellularization of coenocyte. Circle is 60
\\mu m (Dudin et al. 2019). (F) Hydra with actin network, whose nematic
defects determines morphogenesis (Maroudas-Sacks et al. 2021) Scale= 100
\\mu m. ](media/image11.png){width="6.125in"
height="3.0717596237970253in"}

***Actin organization at different scales**:(A) Electron micrograph of
actin cortex of mitotic Hela cells (Kelkar, Bohec, and Charras 2020).
(B) Different forms of actin organization in circular fibroblast cell
(Jalal et al. 2019) Scale*$= 10\mu m$*. (C) Supracellular actin ring
during wound closure (Brugués et al. 2014) Scale*$= 20\mu m$*. (D)
Dorsal closure of amnioserosa with actin network (Ducuing and Vincent
2016) Scale*$= 10\mu m$*. (E) Supra-cellular organization of actin for
cellularization of coenocyte. Circle is* $60\mu m$ *(Dudin et al. 2019).
(F) Hydra with actin network, whose nematic defects determines
morphogenesis (Maroudas-Sacks et al. 2021) Scale*$= 100\mu m$*.*

On the other hand, basal constriction results in opposite curvature, as
observed in the optic cup and mid-hind brain fold of zebrafish (Sidhaye
and Norden 2017; Gutzman et al. 2018). However, convex curvature can
also be produced through basal expansion, as seen in the Drosophila wing
disc (see fig [3.4](#fig_3_4) A). Certain parts of the wing disc can
locally relax the basal side without affecting the apical side, leading
to basal expansion (Sui et al. 2018). In addition to the apical and
basal surfaces, lateral surfaces can also contract or expand due to
myosin II activity, which can cause tissue folding in the wing and leg
discs of Drosophila (Sui et al. 2018; Monier et al. 2015). Furthermore,
cell-cell rearrangements can be produced by altering junction lengths
during germ band extension (Yu and Fernandez-Gonzalez 2016; Collinet et
al. 2015) (see fig [3.4](#fig_3_4) C).

Not only do individual cells undergo coordinated actin reorganization
during epithelial morphogenesis, but supracellular actin structures can
also emerge at the tissue level (see fig [3.3](#fig_3_3) A-C).
Junctional actomyosin organizes to form bundles connected across
multiple cells, allowing for important functions such as wound healing
and morphogenesis (Brugués et al. 2014; Clarke and Martin 2021) (see fig
[3.4](#fig_3_4) D-F). These supracellular networks can exert forces at
the scale of the embryo, as observed in cases such as dorsal closure and
parasegment boundary formation in Drosophila and epiboly in zebrafish
(Ducuing and Vincent 2016; Calzolari, Terriente, and Pujades 2014).
Additionally, these networks can alter the material properties of
specific regions in the embryo, making them more prone to deformation
and thus aiding in the formation of folds or invaginations (see fig
[3.4](#fig_3_4) G).

During Drosophila gastrulation, tissue-level actin cortex is altered in
the direction of the anterior-posterior axis, providing increased
bending strength in that direction. This supports the internalization of
the mesoderm by promoting folding in a perpendicular direction (Yevick
et al. 2019). Interestingly, highly organized actin bundles are also
found in even larger systems such as Hydra, vertebrate smooth muscle,
and the heart (Maroudas-Sacks et al. 2021; Palmer et al. 2021; Cetera et
al. 2014; Helm et al. 2005) (see fig [3.3](#fig_3_3) D-F). These bundles
assist in generating mechanical force patterns that create coordinated
tissue movements at a global scale.

[]{#fig_3_4 .anchor}![Morphogenesis driven by actin at tissue scale: (A)
Apical contraction or basal relaxation both results in the same
curvature. (B) However, amount of deformation will depend on the
contractility gradient. (C) Lateral surface of cells can also undergo
expansion or contraction leading to cell rearrangements or tissue
folding. (D-G) Supracellular actin cables plays vital role in creating
boundaries or causing large scale deformations. Adapted from (Clarke and
Martin 2021) ](media/image12.png){width="6.125in"
height="2.9190474628171477in"}

**Morphogenesis driven by actin at tissue scale**: (A) Apical
contraction or basal relaxation both results in the same curvature. (B)
However, amount of deformation will depend on the contractility
gradient. (C) Lateral surface of cells can also undergo expansion or
contraction leading to cell rearrangements or tissue folding. (D-G)
Supracellular actin cables plays vital role in creating boundaries or
causing large scale deformations. *Adapted from (Clarke and Martin
2021)*

### Timescales of the actin cytoskeleton

Morphogenesis, the process of shaping and forming living structures,
occurs at varying timescales and requires the cell cytoskeleton to
change its shape accordingly. Rheological and mechanobiological
experiments have given us insights into how cells respond to forces and
deformations based on their magnitude and rate (see fig [3.5](#fig_3_5)
A; reviewed in (T. Wyatt, Baum, and Charras 2016)).

For fast deformations (in the range of milliseconds to seconds), cells
exhibit predominantly elastic behavior, as there is insufficient time
for the actin cortex to respond or remodel (Deng et al. 2006). The
cytoskeleton can store elastic energy and release it. At this scale,
there is also flow of cytosol through the cortical mesh, resulting in
poroelastic behavior(Moeendarbary et al. 2013).

When forces or deformations are applied over longer timescales (seconds
to minutes), cells exhibit an increasingly viscoelastic behavior
(Kollmannsberger and Fabry 2011). The actin cortex can flow and is
unable to fully store energy. The actin filaments and crosslinkers, such
as myosins and actinin, allow the cytoskeleton to remodel in response to
mechanical perturbations through turnover in tens of seconds or a few
seconds, respectively. Myosin mini filaments, however, can take longer
to remodel, up to hundreds of seconds.

At even longer timescales (minutes to hours), cells or tissues may
respond through oriented division or rearrangement, allowing them to
adapt to persistent forces such as gravity or surface tension. Tissues
may resemble a viscous fluid and morph into a sphere, such as a
blastocyst. Interactions with the extracellular matrix over hours can
lead to adjustments in the constitutive tension of tissues based on
biophysical and biochemical forces (Porazinski et al. 2015).

[]{#fig_3_5 .anchor}![Molecular pathway and timescale of actin network
related processes: (A) Timescales of different actin driven cellular
processes, ranging from cytoskeletal fluid deformation to large-scale
tissue deformations. (B) Molecular signaling of RhoGTPase. RhoGEFs
return GDP for GTP to activate RhoA. In turn RhoA results in actomyosin
contractility. Adapted from (Kelkar, Bohec, and Charras 2020; T. Wyatt,
Baum, and Charras 2016). ](media/image13.png){width="6.125in"
height="4.7084919072615925in"}

**Molecular pathway and timescale of actin network related processes**:
(A) Timescales of different actin driven cellular processes, ranging
from cytoskeletal fluid deformation to large-scale tissue deformations.
(B) Molecular signaling of RhoGTPase. RhoGEFs return GDP for GTP to
activate RhoA. In turn RhoA results in actomyosin contractility.
*Adapted from (Kelkar, Bohec, and Charras 2020; T. Wyatt, Baum, and
Charras 2016)*.

### Controlling cortical tension

The magnitude of contractile or tensile forces exerted by cells is
greatly influenced by the tissue type and its environment. The signaling
pathways regulating the crosslinkers and nucleators of actin bundles are
responsive to both external biochemical and biomechanical stimuli (see
fig [3.5](#fig_3_5) B; reviewed by (Kelkar, Bohec, and Charras 2020)).
The actomyosin bundles, made up of dynamic actin filaments, constantly
undergo cycles of contraction, polymerization, and depolymerization,
which maintain a homeostatic level of cortical tension in healthy
tissues. As a result of the numerous components involved in the actin
network, cortical tension can be readily modulated by pharmacological
interventions targeting specific molecular targets (Cartagena-Rivera et
al. 2016).

For example, the use of Latrunculin, which binds to actin monomers, can
result in the depolymerization of the actin network and reduce
contractility. Similarly, inhibiting myosin activity with Blebbistatin
leads to a decrease in cortical tension due to its hindrance of myosin
II ATPase activity. Conversely, Calyculin-A enhances contractility by
accelerating the rate of Myosin II phosphorylation. The stability of the
actin network can also be impacted by sequestering ARP 2/3 monomers with
CK666, which increases cortical tension. Other factors, such as
Rho-GTPases and calcium levels, located further along the signaling
pathway, can also affect network stability (Valon et al. 2017).

Optogenetic tools offer a more refined and localized means of
controlling contractility. For instance, tools based on the regulation
of RhoA can be used to locally regulate cell protrusion, tissue tension,
and traction (Valon et al. 2017). A recently developed tool controlling
Shroom3 provides even finer control over apical constriction and can be
used to recreate tissue folding (Martínez-Ara et al. 2022).

### Modeling active tissue dynamics

The advancement of molecular biology and tissue dynamics has increased
our understanding of morphogenesis. However, it is becoming increasingly
crucial to interpret biological experiments through theoretical models
in order to generate new hypotheses and validate them through further
experimentation.

Mathematical models at multiple scales are used to describe both physics
and biology. At larger tissue scales, hyperelastic continuum material
models could be utilized to describe the behavior of the cardiovascular
system (Holzapfel, Ogden, and Sherifova 2019). On smaller scales,
agent-based models are used to explain epithelial tissue behavior in
terms of cell sorting and reorganization (Voss-Böhme 2012). This section
aims to provide the reader with a brief overview of the relevant
modeling approaches in this field.

[]{#fig_3_6 .anchor}![D'Arcy Thompson's forms of tissues: (A-B) Thompson
equates cell aggregates to coalescence of bubbles like in a froth. (C) A
dragon fly wing is a clear example of this organization. Adapted from
(Thompson 1979) ](media/image14.png){width="6.125in"
height="1.5043602362204724in"}

**D'Arcy Thompson's forms of tissues:** (A-B) Thompson equates cell
aggregates to coalescence of bubbles like in a froth. (C) A dragon fly
wing is a clear example of this organization. *Adapted from (Thompson
1979)*

#### Vertex models

D'Arcy Thompson, in his chapter on "The Forms of Tissues," presents an
intuitive argument regarding the role of surface tension or capillarity
in organizing cells into a tissue (Thompson 1979; Graner and Riveline
2017). He observed this phenomenon in a wide range of biological
systems, from two connected cells to the organization of cells in a
dragonfly wing, which resemble the associations of soap bubbles or foams
(see fig [3.6](#fig_3_6)). [^5] In the case of monolayered epithelial
tissue, its polygonal cellular pattern on its surface enables the easy
description and tracking of cell motion and shape change through the use
of vertices and edges.

r5.5cm

![image](media/image15.png){width="2.165353237095363in"
height="2.436768372703412in"}

Vertex models have proven to be valuable in understanding the complex
interactions between cellular shape, the forces generated within
epithelial cells, and the mechanical constraints imposed on the tissue
from external sources (as reviewed in (Alt, Ganguly, and Salbreux
2017)). These models can be two-dimensional or three-dimensional,
depending on the system being modeled, but cells are consistently
defined as having both an apical and basal surface, as well as lateral
interfaces between neighbors. Further complexities have been added to
describe specific systems, such as intercalations in three-dimensional
epithelia, through the use of a geometric shape known as the Scutoid
(reviewed in (Gómez-Gálvez et al. 2021)).

To determine the motion of the vertex, mechanics must be specified. It
is often done using the virtual work function (W). There are two
components: internal $\left( \delta W_{i} \right)$ and external
$\left( \delta W_{e} \right)$.

$$\delta W = \delta W_{i} + \delta W_{e}.$$

The changes in internal virtual work, $\left( \delta W_{i} \right)$ can
result from changes in the cell volumes $(\delta V)$, in the areas of
surfaces $(\delta A)$, or in the lengths of bonds $(\delta l)$. By
defining the cell pressure $(P)$, the surface tension $(T)$, the line
tensions $(\Lambda)$, and internal dissipative forces
$\left( f_{i} \right)$, the differential of the internal virtual work
for vertex movements can be written.

$$\delta W_{i} = \Sigma_{cell\ \alpha}\left( - P^{\alpha}\delta V^{\alpha} \right) + \Sigma_{surface\ k}\left( T^{k}\delta A^{k} \right) + \Sigma_{edge\ \lambda}\left( \Lambda^{\lambda}\delta l^{\lambda} \right) - \Sigma_{vertex\ \nu}\left( f_{i}^{\nu}\delta x^{\nu} \right).$$

Similarly, the external virtual work, $\left( \delta W_{e} \right)$, can
be written according to the external forces $\left( f_{e} \right)$ that
come from external mechanical forces applied to the tissue through the
matrix, or fluid pressure acting on apical or basal cell surfaces.

$$\delta W_{e} = - \Sigma_{vertex\ \nu}\left( f_{e}^{\nu}\delta x^{\nu} \right).$$

The state of a monolayer is determined by minimizing the virtual work
function, taking into account the molecular complexities that contribute
to surface tension and line tensions. In the context of epithelial
layers, the actin cortex significantly impacts the tensions along the
edges. Vertex model simulations in 2D models demonstrate the important
role of interfacial tensions in shaping cell orientation, coordinating
collective migration, and facilitating tissue rearrangement through cell
division.

In contrast, 3D models capture the physics of various morphogenetic
processes, such as the formation of appendages on the drosophila
eggshell and the mechanical compartmentalization of intestinal epithelia
(Osterfield, Berg, and Shvartsman 2017; Pérez-González et al. 2021).
These models offer unique insights into cell packing and the transition
between jamming and unjamming (Park et al. 2015; Tang et al. 2022). In
some cases, phase transitions from a solid to fluid state result from
localized proliferation and oriented divisions, showing that the
epithelial tissue behaves as an active material (reviewed in (Lenne and
Trivedi 2022)).

#### Continuum models

The viscoelastic properties of tissues are captured in vertex models,
which are useful for smaller scale. However, for larger scale
deformations or flows, we can model tissues as a continuous material.
There are two tactics for thinking about these models: one focuses on
the rheological properties of the tissue, and the other on shape
transformations. By thinking of a continuous sheet of cells as an active
surface, we can capture the physics of single cells to embryos (Salbreux
and Jülicher 2017; Khoromskaia and Salbreux 2023).

Continuum models focus on developing reliable constitutive relations and
solving initial-boundary-value problems. Constitutive relations describe
how materials respond to applied loads, and they depend on the internal
constitution of the material. Determining constitutive relations for
epithelial monolayers can be challenging because these tissues are much
more complex than simple metals or passive polymers (see fig
[3.7](#fig_3_8) A-B). However, their complex material behavior can be
understood by characterizing their mechanical response using standard
material testing techniques (Humphrey 2002). Typically, they can be
probed mechanically in a biologically relevant manner, such as through
biaxial or uniaxial stretching experiments that simulate *in vivo*
tissue behavior (Humphrey, Dufresne, and Schwartz 2014). These
experiments with epithelial tissues have revealed the viscoelastic
nature of these materials (A. R. Harris et al. 2012; Khalilgharibi et
al. 2019).

Solids, such as rubber, are considered to have elastic properties,
allowing them to deform reversibly when subjected to a force.
Conversely, fluids are characterized by their viscosity, meaning they
flow in response to an applied force. Viscoelastic materials exhibit
both solid-like and fluid-like behaviors (see fig [3.7](#fig_3_8) C).
Simple models can represent these behaviors by combining elastic
components, represented as springs, and viscous components, represented
as dashpots. The elastic response does not dissipate energy, unlike the
viscous response.

$$\sigma = E\epsilon,\ \ \ \ \sigma = \eta\frac{d\gamma}{dt}.$$

Other material properties like stiffness or Poisson's ratio can be
revealed through quasi-static stretching or compression. However,
dynamic properties are better understood through frequency sweep, creep,
or stress relaxation experiments (Guimarães et al. 2020). Rheological
experiments have been extremely valuable in gaining insight into the
mechanical response of various biological materials, ranging from
reconstituted cytoskeletal proteins to large multicellular aggregates
(Mofrad 2009; Cavanaugh et al. 2020; Xi et al. 2018).

Rheological properties are often linked to physiological state and are
crucial for their specific functions (Park et al. 2015; Vedula et al.
2012). For example, many fundamental shape transitions in embryos occur
through abrupt change in tissue material properties. (Hannezo and
Heisenberg 2022). Therefore, it is important to assess rheological
properties in different microenvironments. Mechanical information such
as deformation, deformation rates or velocity fields, traction forces
exerted by cells on substrates, and intercellular mechanical stress can
provide a more complete picture of tissue rheology when combined with
information about cellular architecture obtained through imaging
(Roca-Cusachs, Conte, and Trepat 2017). These types of experiments shed
light on the complex mechanisms of strain stiffening and viscoelastic
behavior at different deformation regimes involving various parts of the
cytoskeleton.

[]{#fig_3_8 .anchor}![Stress strain behavior of materials: (A) materials
being stretched or compressed. (B) Quasistatic deformations yield
stress-strain curves. (C) Creep test where strain response is
characterized at constant stress.
](media/image16.png){width="5.484139326334208in"
height="1.6777952755905512in"}

**Stress strain behavior of materials**: (A) materials being stretched
or compressed. (B) Quasistatic deformations yield stress-strain curves.
(C) Creep test where strain response is characterized at constant
stress.

However, in certain cases like modeling cardiovascular mechanics or the
growth of organs, we can rely on hyperelasticity or composite material
framework. The basic kinematics assumes a mapping, $x = \chi(X,t)$,
deformation from reference to deformed configuration. The deformation
gradient and Green's strain tensor are defined.

$$F = \nabla_{X}\left( \chi(X,t) \right));\ \ \ \ E = \frac{\left( F^{T}F - I \right)}{2}.$$

The elastic and growth can be delineated in the deformation gradient
through decomposition.

$$F = F_{e}F_{g}.$$

Here, in the theoretical framework of finite elasticity, one can assume
a strain energy function relates to stress. The stress-strain data
extracted from the experiment allows for predicting the form of the
strain energy function.

$$S = \frac{\delta W}{\delta E}.$$

The utilization of hyperelastic models has proven to be effective in
capturing the material response in various biological tissues, such as
the bladder, heart tissue, skin, and arteries (Holzapfel 2000). This
type of formulation provides a degree of flexibility, as it allows for
the inclusion of additional physical constraints, such as the anisotropy
of the tissue microstructure or its incompressibility. Minor
modifications to these constitutive relations can be used to capture the
material response, such as explaining the phenomenon of strain
stiffening, or accounting for the inhomogeneity in the material, such as
the collagen content and crosslinking in the tissue (Holzapfel, Ogden,
and Sherifova 2019).

These models are also employed in the understanding of growth and
remodeling, through the use of kinematical growth theory (Ambrosi et al.
2019). This theory highlights the existence of residual stresses in
growing tissues, which allow for compatible elastic and inelastic
growth-induced deformations, leading to a modification of the tissue
properties into a spatially inhomogeneous and anisotropic state. This
process is of great significance in the field of solid tumor growth
mechanobiology, as the residual stresses directly impact tumor
aggressiveness, nutrient pathways, necrosis, and angiogenesis.

#### Active surface models

At the cellular level, the mechanical properties of tissues are largely
determined by the biopolymeric cytoskeleton, which consists of filaments
and cross-linkers and molecular motors. These components continuously
convert energy, ATP to ADP, through contractions or extensions of the
network, resulting in a physical gel-like system due to its cross-linked
actin filament network. However, the presence of phenomena such as
treadmilling, active polymerization-depolymerization of filaments, and
the mobility of molecular motors, such as myosin, makes the tissue
system an active gel that lacks time-reversal symmetry due to its
continuous energy transduction.

Additionally, the filaments are polar, which allows for the acquisition
of orientational order. This has led to the modeling of tissues as
active gels, similar to modeling active systems, such as flocks of birds
and schools of fish, using hydrodynamics of active matter (Jülicher,
Grill, and Salbreux 2018). Active matter systems are a subclass of
continuum models used to describe the dynamics of packed active
particles, which are based on the liquid crystal theories of soft
condensed matter. Like liquid crystals, cells also possess orientation
and the ability to move past each other. In this framework, the
orientation of filaments in the cytoskeleton or the elongation of cells
in the tissue can be characterized by a nematic order parameter matrix
(see fig [3.8](#fig_3_10)).

$$Q = \frac{3S}{2}\left( n \otimes n - \frac{I}{3} \right),\ \ \ \ S = \lbrack cos2\theta\rbrack,$$

$$\sigma_{active} = \zeta Q.$$

[]{#fig_3_10 .anchor}![Active nematics: Schematics of (A) nematic or
polar particles, (B) extensile and contractile force dipoles, (C)
Various types of defects and related motion of cells Adapted from (Xi et
al. 2018). ](media/image17.png){width="6.125in"
height="1.7378674540682415in"}

**Active nematics**: Schematics of (A) nematic or polar particles, (B)
extensile and contractile force dipoles, (C) Various types of defects
and related motion of cells *Adapted from (Xi et al. 2018)*.

The utilization of this formulation is significant in characterizing the
active forces produced by the network. The stress is separated into two
components: active and passive. The passive stress arises from the
viscoelasticity of the material and the bending, splaying, and twisting
of the aligned elements. The active stress, on the other hand, is
calculated by combining the strength of activity, represented by the
parameter zeta, and the nematic order matrix. The sign of zeta
determines the type of force dipole generated; a negative sign results
in contraction of the system, while a positive sign leads to expansion
along the nematic axis.

The active stress plays a crucial role in the motion of the system and
can result in chaotic motion even in low Reynolds number systems, as
evidenced in dense bacterial systems of *Bacillus subtilis* where jet
flows and turbulent patterns have been observed, as well as in expanding
monolayers where independent vortices have been recorded (Wensink et al.
2012; Blanch-Mercader et al. 2018). The nematic formulation have proven
to be effective in capturing the physics of 2D confined systems and
expanding systems (reviewed in (Saw et al. 2018)).

In the context of 3D models, active surfaces are used to describe the
actomyosin cortex near cell membranes or epithelium in embryos (Salbreux
and Jülicher 2017). This thin sheet of matter generates internal forces
and torques that drive shape changes at the cellular or tissue level.
The resulting three-dimensional structures can be conceptualized as
curved, active two-dimensional surfaces. Forces and torques can be
defined in terms of tension ($t$) and moment ($m$), and the model also
considers the mirror and rotation symmetries of the surface elements
(see fig [3.9](#fig_3_9)).

[]{#fig_3_9 .anchor}![Active surface models: (A) Tissues or cell
surfaces can be modeled as surface with stresses and torques along the
thickness. (B) Internal and external forces actin on a surface element.
The kinematics of these surfaces, mathematical tools from differential
geometry can be applied, using generalized coordinates (\\mathbf{X}),
metric tensor (\\mathbf{g}), and curvature tensor (\\mathbf{C}), where
(dl) is the length of the line element with tangential unit vector (v).
Adapted from (Salbreux and Jülicher 2017)
](media/image18.png){width="3.388980752405949in"
height="2.8280457130358707in"}

**Active surface models**: (A) Tissues or cell surfaces can be modeled
as surface with stresses and torques along the thickness. (B) Internal
and external forces actin on a surface element. The kinematics of these
surfaces, mathematical tools from differential geometry can be applied,
using generalized coordinates ($\mathbf{X}$), metric tensor
($\mathbf{g}$), and curvature tensor ($\mathbf{C}$), where ($dl$) is the
length of the line element with tangential unit vector ($v$). *Adapted
from (Salbreux and Jülicher 2017)*

Salbreux and Julicher's work has demonstrated that flat active membranes
with up-down asymmetry exhibit stability dependent on active tension and
active tension-curvature coupling term. This tension-curvature
dependency has been observed in the pancreas of mice, where the
morphology of epithelial tumors is determined by the interplay of
cytoskeletal changes in transformed cells and the existing tubular
geometry (Messal et al. 2019). Specifically, small pancreatic ducts
produced exophytic growth, whereas large ducts deformed endophytically,
consistent with theoretical predictions. Another example shows that
curls of high curvature form spontaneously at the free edge of suspended
epithelial monolayers, which originate from an enrichment of myosin in
the basal domain that generates an active spontaneous curvature
(Fouchard et al. 2020). The extent of curling is controlled by the
interplay between internal stresses in the monolayer.

While the molecular level behind epithelial morphogenesis, specifically
the actin cytoskeleton, is well understood, there are still gaps in the
theoretical and experimental framework that can bridge the gap between
molecular dynamics and tissue-scale deformations. Vertex and continuum
models have been developed to capture the physics of morphogenesis at
the tissue scale, and phenomenological experiments provide insights into
the constitutive relations of cytoskeletal components and tissues in
specific conditions. However, combining vertex models and active surface
mechanics could provide finer control over individual cell surfaces,
enabling more precise bottom-up morphogenesis.

## Bottom up morphogenesis

### Learn by building

The mechanics and biology of epithelial tissues are complex, with
mechano-chemical signaling and multiscale behavior all intertwined. The
lens of active material has been instrumental in illuminating the role
of molecular elements in undergoing shape changes during morphogenesis.
Mechanistic understanding has been enhanced with new mathematical tools
and advanced microscopy, enabling measurement of the forces involved in
tissues.

The traditional and successful method for studying mechanics has been to
deconstruct the system one component or parameter at a time. By
manipulating genes or disrupting cellular processes, we can observe how
mechanics change. This perturbative method allows for the alteration of
biological systems at various levels, from molecular to tissue, (see fig
[4.1](#fig_4_1)) .

However, studying systems like organoids or embryos can only provide
limited physical insights into the topological transitions of these
structures, as experimental systems have limited physical control and
ability to measure forces. An alternative approach is to learn by
actively performing morphogenesis or reconstructing biological
structures from their basic components.

[]{#fig_4_1 .anchor}![A conceptual representation of two approaches to
understanding mechanics: reconstruction (bottom-up) and deconstruction
(top-down). In reality, they are not separate from each other. These
methods inform each other, with past top-down research guiding new
reconstruction, and new engineered cells or tissues furthering our
understanding of the field in innovative directions.
](media/image19.png){width="6.125in" height="2.9381856955380576in"}

**A conceptual representation of two approaches to understanding
mechanics: reconstruction (bottom-up) and deconstruction (top-down).**
In reality, they are not separate from each other. These methods inform
each other, with past top-down research guiding new reconstruction, and
new engineered cells or tissues furthering our understanding of the
field in innovative directions.

For years, researchers have broken down biological systems into
approachable parts - tissues, cells, proteins - in order to understand
the behavior of each component. However, combining existing knowledge of
these parts to recreate novel experimental systems could reveal the
basic building blocks and effects of scale. This approach would
complement top-down approaches in developmental biology. Synthetic
biology, a perfect example of reconstruction, seeks to recreate life at
various scales, from synthetic proteins to entire cells, in order to
gain a deeper understanding of the indispensable components of life.

As active agents exist at every scale, emergent properties can appear at
higher scales. Thus, it is essential to focus on higher scales or work
with collectives of cells. This reminds me of the example of cars and
traffic: Imagine you know the behavior of all individual car components,
but this information is not sufficient to understand the behavior of
traffic flow. This requires a higher level of analysis. [^6] Similarly,
biological structures exhibit numerous collective behaviors, such as
jamming, nematic order, instabilities, or self-organization (Trepat and
Sahai 2018).

Recreating structures from scratch also provides an opportunity to
understand the role of physics at different scales. In the spirit of
D'Arcy Thompson, we can explore the fundamental properties of matter in
biological structures. [^7] For instance, we can study the role of
surface tension in guiding the shape of cellular aggregates or lumens.
In this work, we focus on the mesoscale structures of epithelia
$\left( \sim 10 - 10^{4}\mu m \right)$.

We present our efforts to engineer an epithelial structure with a
controlled microenvironment that is sensitive to self-organization and
mechanical instabilities. The following sections will describe the ways
of creating these structures from minimal ingredients.

### How to build tissue structures?

Before embarking on the construction of a tissue structure, it is
important to consider the desired form and function. Despite the
diversity in the shapes and functions of tissues, certain elementary
shapes can be seen in many cases, resulting from the interplay between
physical forces and biochemical signaling. Examples of such shapes
include spherical blastocysts, ellipsoidal embryos, or cylindrical
vessels.

After considering the desired form and function of the structure,
established cell lines are selected and synthetic structures are
constructed using various techniques, such as geometry control and
localized folding, as discussed in the [2.3](#mechanobiology) section.
The resulting structures can be further studied to understand the
interplay between physical forces and biochemical signaling, as well as
their potential applications in various biological systems.

#### Controlling geometry and physical forces

From an engineering perspective, scaffolding is a commonly used approach
for constructing synthetic epithelial structures. Scaffolds can be
generated through 3D printing or microfabrication techniques, and cells
can then be seeded onto the scaffold to attain the desired shape (Torras
et al. 2018). This method allows for the creation of a well-controlled
microenvironment for the cells in terms of geometry, stiffness, adhesion
proteins, and cell culture media (see fig [4.2](#fig_4_2) A) .
Structures generated through this approach can be utilized to
investigate tissue behavior in response to forces and curvature.

For instance, cells can be used to form a micro-vessel using a hydrogel
with a cylindrical hole (Dessalles et al. 2021). The hydrogel and cells
were housed in a microfluidic device that controlled pressure and flow
in the vessel, and the authors were able to examine the role of hydrogel
poroelastic properties in regulating the dynamics of the vessel. Another
exciting study demonstrated the potential of epithelial tissues to form
shape-programmable materials by using a collagen scaffold (Mailand et
al. 2022).

Scaffolds can also be designed to dynamically change their shape (see
fig [4.2](#fig_4_2) B). For example, a cell monolayer on a flexible
membrane can alter its curvature (Blonski et al. 2021), and a
combination of stretching and unstretching a cell-laden hydrogel can
produce distinctive folds and patterns (H. F. Chan et al. 2018). In some
cutting-edge studies, researchers have utilized 4D bioprinting, where 3D
printed objects undergo transformation over time (Arif et al. 2022). For
instance, a flat hydrogel sheet containing endothelial cells and
photo-crosslinking can be transformed into a tube (Zhang et al. 2020).

[]{#fig_4_2 .anchor}![Controlling geometry and physical forces: The
concept of scaffolding can be divided into two categories: static and
dynamic scaffolds. (A) Static scaffolds are microfabricated structures
that cells can adapt to and respond to geometrical cues, leading to the
formation of a specific tissue organization (Brassard et al. 2021). (B)
In contrast, dynamic scaffolds consist of cell-laden matrices that are
deformable, and their curvature can change dynamically due to external
pressure or mechanical forces (Blonski et al. 2021; H. F. Chan et al.
2018). (C) Biohybrid assemblies can incorporate active contraction or
pushing to create hybrid structures, such as origami folding triggered
by fibroblast contraction (He et al. 2018), or cells carving out an
intestinal crypt-like geometry from a softer matrix (Nikolce Gjorevski
et al. 2016).](media/image20.png){width="6.125in"
height="3.3014687226596675in"}

**Controlling geometry and physical forces:** The concept of scaffolding
can be divided into two categories: static and dynamic scaffolds. (A)
Static scaffolds are microfabricated structures that cells can adapt to
and respond to geometrical cues, leading to the formation of a specific
tissue organization (Brassard et al. 2021). (B) In contrast, dynamic
scaffolds consist of cell-laden matrices that are deformable, and their
curvature can change dynamically due to external pressure or mechanical
forces (Blonski et al. 2021; H. F. Chan et al. 2018). (C) Biohybrid
assemblies can incorporate active contraction or pushing to create
hybrid structures, such as origami folding triggered by fibroblast
contraction (He et al. 2018), or cells carving out an intestinal
crypt-like geometry from a softer matrix (Nikolce Gjorevski et al.
2016).

Additionally, the contractility of fibroblasts and hepatoma cells has
been utilized to fold 2D structures into 3D shapes (He et al. 2018) (see
fig [4.2](#fig_4_2) C) . Microplates with an origami folding pattern are
created, and the cells apply forces to generate a 3D structure. In other
scenarios, cells are allowed to self-organize through the imposition of
geometric constraints, which enhances the efficiency of organoid-like
systems (Nikolce Gjorevski et al. 2016). In the case of intestinal
organoids, controlling the stiffness of the matrix in specific regions
leads to growth and differentiation at softer areas, producing a highly
reproducible structure (N. Gjorevski et al. 2022).

#### Manipulating biochemical signaling

Another approach to constructing biological structures involves
controlling biochemical signaling to induce shape transformation. This
approach utilizes natural processes in embryo morphogenesis, such as
apical constriction in ventral furrow formation or cell jamming in the
normal elongation of the zebrafish. Optogenetic tools, such as
controlling Rho signaling, can be used to induce localized apical
constriction with spatiotemporal control (Izquierdo, Quinkler, and De
Renzis 2018). This technique can also be applied to other proteins, such
as Shroom3, to induce synthetic morphogenesis in neural organoids
(Martínez-Ara et al. 2022) (see fig [4.3](#fig_4_3) C).

Epithelial-mesenchymal interaction is another crucial aspect of the
tissue folding process. Hughes et al. demonstrated that cell clusters
can remodel the matrix to create oriented stresses that lead to budding
in tissues (Hughes et al. 2018). By controlling the location and density
of these cell clusters, it is possible to manipulate the curvature of
the epithelia. Mesenchymal condensation serves as a folding template for
the final tissue structure (Palmquist et al. 2022; Shyer et al. 2017)
(see fig [4.3](#fig_4_3) B).

The microenvironment plays a critical role in providing vital signals to
tissues and can be manipulated to activate specific cellular functions.
Microfluidic techniques can deliver appropriate morphogen gradients to
the tissue with precise timing (Hofer and Lutolf 2021). *In vivo*,
multiple morphogens often act simultaneously. For instance, during
neural tube development, there is an opposing gradient of sonic hedgehog
(SHH) and bone morphogenic protein (BMP). With microfluidic devices,
stable gradients can be generated, even in opposite directions (Demers
et al. 2016), thus mimicking symmetry-breaking events and directional
neural tube patterning (see fig [4.3](#fig_4_3) D).

Moreover, genetic engineering of specific cells can be utilized to
control signaling. Human pluripotent stem cells (hPSCs) can be
programmed to express SHH (Cederquist et al. 2019) (see fig
[4.3](#fig_4_3) E). Mixing these cells with others could result in a
polarized organoid and a patterned cerebral organoid.

[]{#fig_4_3 .anchor}![Manipulating biochemical signaling: Biochemical
signaling and mechanics are interdependent in morphogenetic processes
(A). The transport of signaling molecules can affect the cytoskeleton
and mechanical properties of cells, while mechanical forces can also
influence biochemical signaling. Microfluidics (D) is one method used to
control biochemical signaling by providing opposing morphogen gradients
through multiple channels (Demers et al. 2016). Alternatively, cells can
be genetically engineered to undergo apical constriction (C) or produce
morphogen gradients (E) locally to form curved geometries (Martínez-Ara
et al. 2022; Cederquist et al. 2019). Mesenchyme condensation (B) is
another approach used to program curvature in developing tissues (Hughes
et al. 2018; Palmquist et al. 2022).](media/image21.png){width="6.125in"
height="3.228946850393701in"}

**Manipulating biochemical signaling:** Biochemical signaling and
mechanics are interdependent in morphogenetic processes (A). The
transport of signaling molecules can affect the cytoskeleton and
mechanical properties of cells, while mechanical forces can also
influence biochemical signaling. Microfluidics (D) is one method used to
control biochemical signaling by providing opposing morphogen gradients
through multiple channels (Demers et al. 2016). Alternatively, cells can
be genetically engineered to undergo apical constriction (C) or produce
morphogen gradients (E) locally to form curved geometries (Martínez-Ara
et al. 2022; Cederquist et al. 2019). Mesenchyme condensation (B) is
another approach used to program curvature in developing tissues (Hughes
et al. 2018; Palmquist et al. 2022).

#### Exploiting mechanical instabilities

[]{#fig_4_4 .anchor}![D'Arcy Thompson compares biological budding to
splashes (A) of fluids and Rayleigh-Plateau instability (Thompson 1979)
(B), where liquid splits up into smaller droplets. This mechanism could
also be seen in organogenesis of mammary tissue (C, D) (Fernández et al.
2021).](media/image22.png){width="6.125in"
height="1.5883541119860018in"}

**D'Arcy Thompson compares biological budding to splashes** (A) of
fluids and Rayleigh-Plateau instability (Thompson 1979) (B), where
liquid splits up into smaller droplets. This mechanism could also be
seen in organogenesis of mammary tissue (C, D) (Fernández et al. 2021).

Morphogenesis, the process of shaping and formation of biological
structures, often involves spontaneous pattern formation or
symmetry-breaking events (Ishihara and Tanaka 2018). These processes are
often dictated by mechanical instabilities, which can lead to large
deformations in soft matter systems. In material science, these
instabilities are typically seen as problematic as they cause rapid
breakage. However, in soft matter, large deformations can lead to
interesting topological transformations, providing an opportunity for
engineers to exploit these instabilities in the development of new
actuators or soft robots (reviewed in (Pal et al. 2021)). [^8]

The significance of mechanical instabilities was foreseen by D'Arcy
Thompson in his comparison of fluid splashes to hydroids (see fig
[4.4](#fig_4_4) A). He wrote that the shapes of a potter's cup, glass
blower's bulb, and biological structures are simply glorified splashes
formed slowly under conditions of restraint that enhance or reveal their
mathematical symmetry (Thompson 1979). [^9] This conjecture has been
confirmed through numerous quantitative studies on various systems,
including ripples in leaves and wrinkles in the brain (Liang and
Mahadevan 2009; Karzbrun et al. 2018).

There are various instabilities associated with solids and fluids. For
example, the Rayleigh-Plateau instability explains why a fluid stream
breaks into smaller packets, driven by the fluid's tendency to minimize
its surface area due to surface tension. The same instability can arise
when fluid is surrounded by an elastic medium, instead of air, provided
the surface tensions can overcome the elastic stresses, leading to
budding as observed in alveologenesis in human mammary tissue (Fernández
et al. 2021) (see fig [4.4](#fig_4_4) C-D). However, as tissues are
active viscoelastic materials surrounded by viscoelastic medium, the
timescales of these instabilities change, slowing down to hours instead
of milliseconds in water droplets.

There are several types of mechanical instabilities associated with
solids and fluids, including Rayleigh-Plateau instability,
Kelvin-Helmholtz instability, Rayleigh-Taylor instability, viscous
coiling and folding, and large-scale wrinkling and buckling (Gallaire
and Brun 2017; Kourouklis and Nelson 2018). In this study, we aim to
harness these instabilities to recreate epithelial structures.

Applying compressive stresses is one of the easiest ways to induce
mechanical instabilities in solids. These stresses can occur in
biological systems as a result of differential growth, swelling, or
morphogen gradients and can lead to various forms of instabilities,
including wrinkling, creasing, and buckling. Buckling occurs when a thin
sheet is subjected to in-plane compressive stress, and if the stress is
above a critical value, the sheet undergoes out-of-plane deformation
instead of in-plane shrinkage (see fig [4.5](#fig_4_5) B). In contrast,
wrinkling and creasing occur in similar compressive stresses, but the
thin sheet is typically supported by a compliant substrate.

[]{#fig_4_5 .anchor}![Compressive stresses occur frequently in many
systems (A). We can consider epithelia and matrix as thin sheet
supported by a compliant substrate. Thus, the tissue folding could be
understood as buckling of sheets (B) or wrinkling or creasing of thin
film supported by an hydrogel (C).](media/image23.png){width="6.125in"
height="3.8279647856517935in"}

**Compressive stresses** occur frequently in many systems (A). We can
consider epithelia and matrix as thin sheet supported by a compliant
substrate. Thus, the tissue folding could be understood as buckling of
sheets (B) or wrinkling or creasing of thin film supported by an
hydrogel (C).

The creation of biological tissues *in vitro* has been a subject of
great interest in the field of tissue engineering. To reproduce the
characteristics of these tissues, researchers have turned to the use of
hydrogels. These materials can be mechanically and chemically
manipulated to simulate the behavior of biological matrices, which
provide support for epithelial structures.

One of the ways in which hydrogels can be used to recreate the behavior
of biological tissues is through the application of physical stress. For
example, swelling of the hydrogel can cause it to undergo rapid large
volumetric changes, producing crease-like patterns on the surface. If
the hydrogel is constrained at the bottom, these creases can become
permanent. Alternatively, if the hydrogel is supported by another
flexible material, such as another hydrogel or an elastic substrate, the
stresses produced during swelling will result in a wrinkling instability
(see fig [4.5](#fig_4_5) A). These instabilities are important for
understanding the formation of a variety of structures, including the
gyrification of the brain cortex.

In a study by Tallinen et al., the gyrification of the brain cortex was
replicated through the programming of materials to produce wrinkling
(Tallinen et al. 2016). The researchers created a synthetic brain with
an inner core of an inert elastomer and an outer layer of a swellable
elastomer. On swelling, the outer layer produced folds that closely
matched the process of gyrification (see fig [4.6](#fig_4_6) A).

Similar mechanisms have been observed in other systems undergoing
differential growth, such as the branching of lungs and formation of
intestinal villi (Varner et al. 2015; Shyer et al. 2013) (see fig
[4.6](#fig_4_6) B,D). These findings highlight the potential of
hydrogels as a tool for understanding the physical mechanisms underlying
tissue development. However, it is worth noting that the mechanisms
described here are the subject of ongoing research and debate in the
field of developmental biology.

The ability to recreate biological tissue growth conditions *in vitro*
has been made possible through the use of hydrogels. Researchers have
discovered that by mechanically and chemically controlling the hydrogel,
they can generate desired mechanical instabilities (Dervaux and Amar
2012). This can be accomplished through the swelling or pre-stretching
of the gel, or by manually applying compressive stresses.

One way to simulate growth is through the direct stretching or
compression of the gel. Chan et al. showed that the patterns produced
can be controlled by modulating the shear modulus of the hydrogel with
the epithelial layer and stretch (H. F. Chan et al. 2018) (see fig
[4.5](#fig_4_5) B). By pre-stretching the hydrogel before seeding cells,
they were able to produce folded patterns with different wavelengths
depending on the type of pre-stretching applied (uniaxial or biaxial).

Another type of instability in bilayers is delaminated buckling, which
is often observed in thin film delamination in furniture. This can be
induced through compressive stresses created during growth or collective
tension. Recent studies have shown that growing epithelia confined in a
sphere undergo delaminated buckling after reaching a critical
growth-induced stress (Trushko et al. 2020) (see fig [4.6](#fig_4_6) C),
or through intercellular stresses (Oyama et al. 2021) or by placing a
biofilm on top of the epithelial monolayer (Cont et al. 2020).

[]{#fig_4_6 .anchor}![Examples of mechanical instabilities: (A)
Synthetic mini brains illustrate the wrinkling of the outer layer with
swelling mimicking gyrification (Tallinen et al. 2016). (B, D) Other way
around where inner layer of lung or intestinal epithelia develops folds
when embedded into a hydrogel or muscle shell (Varner et al. 2015; Shyer
et al. 2013). (C) It is also shown that simple epithelial tissues
embedded into a shell would also buckle (Trushko et al. 2020). (D) (T.
P. J. Wyatt et al. 2020) used matrix independent tissue with compression
to illustrate that the epithelial tissue itself can undergo buckling.
Panel A, D are adpated from (Collinet and Lecuit 2021) and C from
(Matejčić and Trepat 2020) ](media/image24.png){width="6.125in"
height="3.109054024496938in"}

**Examples of mechanical instabilities**: (A) Synthetic mini brains
illustrate the wrinkling of the outer layer with swelling mimicking
gyrification (Tallinen et al. 2016). (B, D) Other way around where inner
layer of lung or intestinal epithelia develops folds when embedded into
a hydrogel or muscle shell (Varner et al. 2015; Shyer et al. 2013). (C)
It is also shown that simple epithelial tissues embedded into a shell
would also buckle (Trushko et al. 2020). (D) (T. P. J. Wyatt et al.
2020) used matrix independent tissue with compression to illustrate that
the epithelial tissue itself can undergo buckling. *Panel A, D are
adpated from (Collinet and Lecuit 2021) and C from (Matejčić and Trepat
2020)*

The formation of the ventral furrow in the drosophila embryo can also be
considered as a buckling event. Although there are multiple explanations
for this phenomenon, recent studies have shown that the instability
leading to the fold is caused by embryo-level forces (Guo, Swan, and He
2022; Fierling et al. 2022). Apart from instabilities, it is remarkable
that the mechanical information can be encoded in the substrate. For
instance, the tension produced by the cells in a pre-stretched membrane,
on cutting would lead to curling (Tomba et al. 2022), or through
stretching a suspended epithelial layer would also do the same(Fouchard
et al. 2020).

It is noteworthy that there is currently only one established method for
directly applying compressive stresses to suspended epithelial tissue.
The Lab of Guillaume Charras has developed a technique using a
cell-laden collagen gel sandwiched between two rods, where the gel is
digested with collagenase to create a suspended monolayer (see fig
[4.6](#fig_4_6) E). Through extensive experimentation, they have
observed that the compression of more than 35% strain produces transient
buckling events (T. P. J. Wyatt et al. 2020). Importantly, the actin
cytoskeleton plays a crucial role in buffering deformations in this
system.

### Tissue hydraulics

#### Hydraulic control of morphogenesis

[]{#fig_4_7 .anchor}![Tissue hydraulics plays an essential role in
establishing (A) embryonic axis through lumen coarsening, and later the
pressure regulates the size of the embryo. Laplace's law acts on the
spherical cavities between cells to the whole blastocyst (Dumortier et
al. 2019; Chii Jou Chan et al. 2019; Collinet and Lecuit 2021). (B)
Interestingly, if the inflated structure is surrounded by a mesh you see
a stressball effect, where material inflates through the mesh. Similar
phenomena is visible in growth and inflation of the lizard lungs. The
smooth muscle constrains the deformation leading to stressball
morphogenesis (Palmer et al. 2021). (C) In cnidarians, the different
orientation of F-actin leads to different shapes of the organism
(Stokkermans et al. 2022). ](media/image25.png){width="6.125in"
height="4.977004593175853in"}

**Tissue hydraulics** plays an essential role in establishing (A)
embryonic axis through lumen coarsening, and later the pressure
regulates the size of the embryo. Laplace's law acts on the spherical
cavities between cells to the whole blastocyst (Dumortier et al. 2019;
Chii Jou Chan et al. 2019; Collinet and Lecuit 2021). (B) Interestingly,
if the inflated structure is surrounded by a mesh you see a stressball
effect, where material inflates through the mesh. Similar phenomena is
visible in growth and inflation of the lizard lungs. The smooth muscle
constrains the deformation leading to stressball morphogenesis (Palmer
et al. 2021). (C) In cnidarians, the different orientation of F-actin
leads to different shapes of the organism (Stokkermans et al. 2022).

In this thesis, we focus on the role of hydraulic pressure in
morphogenesis. It has been well established in the field of
developmental biology that fluid pressure plays a significant role in
lumen expansion. For instance, in the mouse embryo, cell aggregates form
small fluid cavities in intercellular junctions, which grow and coalesce
into a large lumen, breaking the symmetry of the embryo, due to the
presence of an osmotic pressure gradient ((Dumortier et al. 2019);
reviewed by (Torres-Sánchez, Kerr Winter, and Salbreux 2021), see fig
[4.7](#fig_4_7) A). This process is powered by the pumping of ions and
water by the cells, which generates pressure in the fluid-filled
cavities, ultimately leading to the formation of spherical embryos. For
any inflated spherical shell, the relationship between pressure
($\Delta P$), curvature ($R$), and surface tension ($\sigma$) can be
described by Laplace's law.

$$\sigma = \frac{\Delta PR}{2}.$$

The shape that is created under pressure depends on the material
properties of the tissue. For example, a homogeneous material would
create a uniform curvature, such as a spherical shape, while an
anisotropic tissue with oriented cells would result in various shapes,
such as cylinders or ellipsoids (Stokkermans et al. 2021) (see
fig[4.7](#fig_4_7) C). An interesting example of this phenomenon can be
seen in the lobed epithelium of lizard lungs, which resembles the shape
of a stress ball. Palmer et al. propose that the smooth muscle network
functions as a mesh that constrains the epithelium, much like the outer
layer of a stress ball (Palmer et al. 2021) (see fig[4.7](#fig_4_7) B).
Upon the application of pressure, the epithelium inflates in the regions
between the gaps in the muscles.

For embryos, an increase in pressure results in an increase in tension
and stretching of the cells. Once a certain threshold is reached, the
cell junctions may leak, causing a reduction in luminal pressure and
shrinkage of the embryonic cavity. This system of pressure regulation
through leakage acts as a mechanism for size regulation (Chii Jou Chan
et al. 2019). At the same time, it polarizes the embryo and promotes
cell segregation and fate specification (see fig[4.7](#fig_4_7) A,
reviewed by (Chii J. Chan and Hiiragi 2020)).

Similar coalescence and lumen coarsening have been observed in other
systems (reviewed in (Schliffka and Maître 2019)). The pressure can also
be generated through secretion of the matrix, as seen in the case of the
drosophila hindgut with mucins (Syed et al. 2012), or through the
secretion of hyaluronic acid in the formation of ear canals in zebrafish
otic vesicles (Munjal et al. 2021). Despite numerous *in vivo*
experiments, there are very few systems in which epithelial tissue can
be subjected to controlled shape and size *in vitro*.

#### Mechanics of domes

[]{#fig_4_8 .anchor}![Historical development of epithelial domes:(A)
Distended epithelium was observed in explant cultures in 1930-50s. (B)
With MDCK cell line, spontaneously forming domes/hemicysts were
characterized (Leighton et al. 1969; Valentich, Tchao, and Leighton
1979). (C,D) In our lab, shape and size of the domes were controlled
with micropatterning adhesion protein (Latorre et al. 2018). The
pressure and tension was measured with Laplace's law and traction force
microscopy. (E-F) For non-spherical domes, curved monolayer stress
microscopy technique was implemented by segmenting the dome shape
(Marín-Llauradó et al. 2022). ](media/image26.png){width="6.125in"
height="5.708583770778652in"}

**Historical development of epithelial domes**:(A) Distended epithelium
was observed in explant cultures in 1930-50s. (B) With MDCK cell line,
spontaneously forming domes/hemicysts were characterized (Leighton et
al. 1969; Valentich, Tchao, and Leighton 1979). (C,D) In our lab, shape
and size of the domes were controlled with micropatterning adhesion
protein (Latorre et al. 2018). The pressure and tension was measured
with Laplace's law and traction force microscopy. (E-F) For
non-spherical domes, curved monolayer stress microscopy technique was
implemented by segmenting the dome shape (Marín-Llauradó et al. 2022).

Many of the morphogenetic events are called doming because the shape
vaguely resemble a spherical cap. For instance, doming of the retina in
the eye or zebrafish embryo, or doming during duct formation of mammary
or salivary glands. There are typically two mechanisms for these: first,
an accumulation of the cells or matrix to create curvature; and second,
trans-epithelial transport causing hydraulic pressure-driven shape
change. The second kind is remarkable as they mimic various lumenized
epithelia *in vivo*.

This is the most pertinent system to the thesis. I would briefly go into
the historical developments in dome mechanics.

Fluid-filled dome formation in epithelial tissue culture has been
recorded since 1933 (Cameron 1953) (see fig [4.8](#fig_4_8) A). After
several decades alongside the development of cell culture techniques,
microscopy, and MDCK cell line [^10], in 1968, Leighton and colleagues
observed that the confluent MDCK cell monolayers formed hemispherical
blisters (domes) (Leighton et al. 1969) (see fig [4.8](#fig_4_8) B).
They observed that these are different from renal tubules because the
apical surface, with microvilli, was facing outwards. They saw that
these fluid-filled structures are dynamically changing size and
curvature. They would burst to deflate and leak fluid out in the medium
(Valentich, Tchao, and Leighton 1979). After sometime, they could heal
and form the dome again. Later, other cell lines derived from mammalian
and amphibian kidneys were often observed to form domes too (Dulbecco
and Okada 1980; Leighton 1981; Lever 1979)

Now the mechanism is clear as the epithelial cells perform critical
barrier function alongside controlling the transepithelial flow of ions
and water. It was shown that hindering sodium-potassium ion pumping
reduces the likelihood of domes (Leighton et al. 1969). Thus, on forming
a confluent monolayer these cells perform their function of pumping ions
from apical to basal direction (Valentich, Tchao, and Leighton 1979). If
the substrate is solid and impermeable the tissue accumulates enough
pressure to delaminate and form a spherical structure.

Most domes observed have been spherical and circular in footprint,
indicating uniform tension across the dome. This can be explained by
considering the dome as a thin shell under pressure, similar to a
bubble, and following Laplace's law. Early studies attempted to infer
tension through geometry and pressure measurement (Tanner, Frambach, and
Misfeldt 1983), finding that the pressure was of the same order as
physiological vessels (see fig [4.9](#fig_4_9) A-B).

[]{#fig_4_9 .anchor}![Methods for measuring pressure and tension: (A)
Earlier studies tried to estimate tension through geometry and thickness
of the monolayer (Tanner, Frambach, and Misfeldt 1983). (B) Later,
pressure was measured by puncturing the dome with a micro-needle.
However, the measurement of pressure is static, because the dome
deflated after the puncturing (Choudhury et al. 2022). (C) Traction
force microscopy technique provides a viable non-invasive solution for
measuring pressure under to domes (Latorre et al. 2018).
](media/image27.png){width="6.125in" height="2.49753280839895in"}

**Methods for measuring pressure and tension**: (A) Earlier studies
tried to estimate tension through geometry and thickness of the
monolayer (Tanner, Frambach, and Misfeldt 1983). (B) Later, pressure was
measured by puncturing the dome with a micro-needle. However, the
measurement of pressure is static, because the dome deflated after the
puncturing (Choudhury et al. 2022). (C) Traction force microscopy
technique provides a viable non-invasive solution for measuring pressure
under to domes (Latorre et al. 2018).

One study (Popowicz, Kurzyca, and Popowicz 1986) identified a "dome
curve" when the frequency of domes was plotted against size, observing
three classes of domes in terms of size. Smaller domes were observed to
swell and increase in size. It was also suggested that there could be
different subpopulations of MDCK cells. In the 1990s, many strains were
characterized that formed different inflated structures, ranging from
normal domes to tubules (Klebe et al. 1995). One cell line, called super
dome MDCK, formed larger domes.

Despite research into ion transport, hormone signaling, the role of
tight junctions, and external shear stress, the understanding of the
mechanics of domes and pressure has remained stagnant due to the lack of
tools for measuring tension, pressure, and controlling the shape and
size of these structures.

The work of Ernest Latorre in our laboratory has led to the development
of a system for controlling the size of domes and studying the
relationship between tension and pressure (Latorre et al. 2018) (see fig
[4.8](#fig_4_8) C-D). By utilizing protein patterning techniques,
Latorre was able to create non-adhesive circular regions on soft PDMS
gel, which, when seeded with MDCK cells, led to the formation of domes.
The gel was embedded with beads to allow for the calculation of traction
forces and pressures exerted by the monolayer (see fig [4.9](#fig_4_9)
C). This system allowed for a deeper understanding of the rheology of
tissue and the role of the cytoskeleton. He observed that stretching the
actin cortex leads to dilution, and that tension reaches a stable value
regardless of strain. He also observed the surprising phenomenon of
superelasticity, where cells are heterogeneously stretched in the dome
when tension is uniform. To further understand the role of actin and
keratin bundles in providing superelasticity, Latorre et al. developed a
vertex model through which they could understand the instability
triggered by actin dilution, and rescued by intermediate filaments.

Ariadna Marin-Llaurado extended Latorre's work by examining domes of
varying sizes and shapes (see fig [4.8](#fig_4_8) E). This study found
that different-sized spherical domes have similar tensions, and that
pressure is compensated according to curvature. Marin-Llaurado couldn't
rely on a simple formula for tension calculation, because the tension in
non-spherical domes is non-uniform (Marín-Llauradó et al. 2022). They
used confocal microscopy to map dome curvature and calculated stresses
computationally using a novel method called cMSM (curved Monolayer
Stress Microscopy) (see fig [4.8](#fig_4_8) F). This method infers
stresses just through geometry and pressure as in Young-Laplace
relation. It does not need to make any assumptions related to material
properties. The results showed that cells tended to align along the
principal stress direction.

The mechanics of osmotic and hydraulic gradients are also crucial to
understand. Chaudhary et al. demonstrated that kidney cells act like a
mechanobiological pump (Choudhury et al. 2022). Using a two-layer
microfluidic chip, the team was able to measure and apply pressure
differences across an epithelial monolayer and observe that the tissue
acted like a mechanical pump that stalls at high pressure. Remarkably,
they discovered that diseased kidney cells pump in a different direction
than healthy ones. They were able to control both osmotic and hydraulic
pressure. Another study by Ishida-Ishihara et al. investigated the
connection between osmotic pressure and extracellular matrix swelling
(Ishida-Ishihara et al. 2020). The researchers found that osmotic
gradients trigger Aquaporin transport channels, leading to dome
formation through Matrigel swelling. However, these domes are gel-filled
structures that differ from fluid-filled domes.

MDCK domes provide a model system for studying transport, cell fate, and
tissue dynamics with a curvature. However, control over luminal pressure
in these structures remains a challenge.

## Structure of the thesis

### What is to be done?

Morphogenesis refers to the process of tissue deformation or growth,
which results from the combination of both endogenous and exogenous
mechanical forces (Valet, Siggia, and Brivanlou 2022; Collinet and
Lecuit 2021). These forces may arise from the contractility of the
epithelium and the surrounding matrix, as well as hydraulic pressure
from the lumen (Torres-Sánchez, Kerr Winter, and Salbreux 2021; Chii J.
Chan and Hiiragi 2020). The various stresses act on different components
of the tissue, such as cells and the extracellular matrix, which exhibit
unique viscoelastic properties and remodeling time scales (Cavanaugh et
al. 2020; Kelkar, Bohec, and Charras 2020; Ambrosi et al. 2019).
However, comprehending how these stresses interact with viscoelastic
properties to bring about particular morphogenetic events in vivo
presents significant technical and conceptual challenges. These
obstacles include disentangling the roles played by distinct components
in a system, a lack of tools for quantitative measurements of stresses
and mechanical properties, and an inability to apply controlled stresses
over a wide range of amplitudes and rates.

In response to these challenges, bottom-up approaches have emerged as a
complementary strategy for understanding the morphogenetic potential of
individual components and building complex, functional tissues
(Trentesaux et al. 2023; Ingber 2018). These approaches have been
successful in engineering basic morphogenetic processes such as
epithelial bending or buckling (Matejčić and Trepat 2022). However, even
though bottom-up approaches are proving to be successful, we still need
tools that can measure and control the shape and stress of 3D epithelia
simultaneously. Additionally, we lack computational models that
integrate cellular and tissue shape with the subcellular determinants of
epithelial mechanics, such as the contractility, turnover, and
viscoelasticity of the actomyosin cortex.

This thesis seeks to address these gaps in knowledge by investigating
the mechanics of epithelial tissues. A comprehensive understanding of
the principles that govern tissue form and function is essential for
both advancing our understanding of fundamental physical rules in
biology and inspiring new engineering tools and design principles. To
achieve this, we leverage cutting-edge technologies, such as 3D
printing, microfluidics, and 3D cell cultures, to individually control
morphogenetic driving factors.

Our approach provides a material science perspective for probing the
intricate mechanisms involved in the generation of forces and shape
changes at the cellular and tissue levels, and holds promise for
discovering emergent phenomena and enabling the building of novel tissue
forms and assemblies.

### Objectives

#### General aim of the thesis

This thesis aims to investigate the mechanics of epithelial layers under
controlled pressure.

#### Specific aims of the thesis

General aims are divided into specific goals:

1.  Develop a novel technology for constructing three-dimensional
    epithelia using lumen pressure control.

2.  Characterize the material response of the pressurized epithelial
    tissue.

3.  Explore the mechanics of epithelial folds.

### Thesis outline

Results are presented in Part 2 with four chapters that address the
specific aims of the thesis and provide a understanding of the mechanics
of epithelial layers subjected to controlled pressure.

-   Chapter 6 details the construction of an experimental system
    designed to physically control epithelial monolayers. This chapter
    showcases the main result of the PhD, a novel microfluidic system
    that generates 3D epithelia with controlled pressure and shape. The
    chapter highlights the successful development of the microfluidic
    system, while also summarizing any failed or attempted methods used
    in constructing the device.

-   Chapter 7 focuses on using the microfluidic device to understand
    epithelial mechanics. The chapter reports the results of rheological
    experiments and relates them to the computational framework. It is
    demonstrated that the shape and rheology of the epithelia are driven
    by the viscoelasticity of the actomyosin cortex.

-   Chapter 8 describes the buckling instability in pressurized
    epithelia. It is found that rapid deflation produces a buckling
    instability that leads to the formation of epithelial folds.
    Buckling occurs across different length scales to overcome
    compressive stresses, and folding patterns become more complex with
    increasing size. The chapter discusses the potential of guiding the
    folds by controlling the shape and size of the epithelia.

-   Finally, in Chapter 9, the findings are summarized with a list of
    conclusions. Along with a brief discussion on future perspectives of
    this thesis.

In summary, the thesis presents a microfluidic-based technique to impose
a controlled deformation on an epithelial monolayer while continuously
monitoring its state of stress. This technique allows for investigation
of the active viscoelasticity of epithelial layers over physiological
time scales. The thesis also presents a 3D model of the epithelium,
which explains the observed phenomena using the active viscoelastic
properties of the actomyosin cortex. Furthermore, it is demonstrated
that these viscoelastic properties, along with adhesion micropatterning,
can be utilized to engineer epithelial wrinkles with predictable
geometry. The results provide an understanding of the mechanics of
epithelial layers subjected to controlled pressure and showcase the
potential of the developed techniques to further explore the synthetic
morphogenesis.

# Results {#results-1}

## A microfluidic device for generating 3D epithelia

### Introduction

To generate three-dimensional epithelial structures in vitro from planar
epithelial monolayers, we chose to utilize an existing system of
epithelial domes (spontaneous domes) developed by Ernest Latorre and
improved by Ariadna Marin-Llauradó (Latorre et al. 2018; Marín-Llauradó
et al. 2022). This system involves seeding a Madin-Darby canine kidney
(MDCK) cell monolayer on a substrate that is patterned with circular
non-adhesive regions. The cells invade these regions and form a cohesive
monolayer everywhere within 24 to 48 hours. Due to the active ion
pumping mechanism of the MDCK cells in the apical-to-basal direction,
the cells delaminate from impermeable substrates such as glass or soft
PDMS gel and form spherical cap structures in the circular patterns,
known as epithelial domes. Latorre and Marin-Llauradó demonstrated that
they could form a variety of structures with controlled shape and size,
ranging from circular to rectangular.

This system also enables the use of 3D traction force microscopy to
measure pressure. The technique involves measuring the deformation of a
soft PDMS gel embedded with beads to characterize the forces and
pressures applied by the cells on the substrate. This method offers an
innovative approach to measuring pressure compared to the previous
technique of puncturing epithelial domes with a microneedle (Tanner,
Frambach, and Misfeldt 1983; Choudhury et al. 2022). It also allows for
the characterization of the rheology of epithelia and the discovery of
interesting material properties such as the superelasticity of cells
during stretching (Latorre et al. 2018).

However, the formation of epithelial domes is dependent on the ion
pumping mechanism of the domes, making them spontaneous structures.
Therefore, the timescales for the dome stretching are not controlled.
This process can be marginally accelerated by a few hours through the
use of drugs like Forskolin, which can activate transepithelial channels
of NA+/K+/Cl- (Klebe et al. 1995; Bourke et al. 1987). However, to build
and physically control the epithelial structure, pressure control is
necessary. In this chapter, we will be discussing a microfluidic chip
that can inflate an epithelial monolayer into a dome while also allowing
us to measure and control the forces involved.

### Monolayer Inflator

Drawing inspiration from the pioneering work on organ-on-chip
microfluidic devices, we have deemed these platforms to be an ideal
system for the precise manipulation of pressure, cell culture
conditions, and the acquisition of high-resolution imaging data (Huh et
al., 2010; Nelson et al., 2017). An illustrative example is the
lungs-on-chip device, which comprises two distinct layers separated by a
porous membrane. The top layer contains a channel for the epithelial
cells, while the bottom layer has a channel for the endothelial cells.
This device is assembled on a thin glass slide, which facilitates the
collection of high-quality imaging data.

Therefore, we conceived the idea of a MOnoLayer Inflator (MOLI) device,
which utilizes a two-layer microfluidic channel with one side for
epithelial monolayers and the other for the application of pressure (see
fig [1.1](#fig_6_1)). The epithelial monolayer side is micropatterned
with a protein that contains non-adhesive or less-adhesive regions for
dome formation. Our working hypothesis postulated that cells would
adhere to the protein substrate uniformly, even in regions with lower
adhesive properties. We anticipated that upon the application of
pressure, cells would detach from the regions with weaker adhesion,
leading to the formation of a dome-shaped structure.

We attempted to fabricate the devices by utilizing plastic stickers and
photopolymerizable adhesive, but encountered difficulties such as fluid
leakage and limited biocompatibility, rendering them unsuitable (Sollier
et al. 2011; Bartolo et al. 2008). Consequently, we opted for the
utilization of PDMS material to construct the microfluidic chip due to
its facile handling and processing characteristics.s

[]{#fig_6_1 .anchor}![Conceptual design of MOLI: (A) Two layer
microfluidic device with porous membrane sandwiched between. (B) Upon
application of pressure, cells from low adhesion will detach to form an
epithelial dome. ](media/image28.png){width="6.125in"
height="2.3681244531933507in"}

***Conceptual design of MOLI**: (A) Microfluidic device consist of a
porous membrane sandwiched between two layers of schannels. (B) Upon
application of pressure, cells from low adhesion will detach to form an
epithelial dome.*

![ 3D printed mold for the device patterned to prepare eight devices at
a time. The thickness of the PDMS block is controlled with volume of
PDMS poured into the mold. After polymerization, the PDMS is cut into
individual pieces and inlets are punched with a biopsy punch.
](media/image29.png){width="6.125in" height="1.5608048993875765in"}

***3D printed mold for the device** patterned to prepare eight devices
at a time. The thickness of the PDMS block is controlled with volume of
PDMS poured into the mold. After polymerization, the PDMS is cut into
individual pieces and inlets are punched with a biopsy punch.*

### Fabrication of the device

The structure of the device consists of four layers: glass, bottom
channel, porous membrane, and top channel. These layers are bonded
together using ozone plasma activation.

For imaging epithelial structures with high-resolution confocal
microscopy, the device must be mounted on a thin glass slide. We used #0
glass slides, which have a thickness range of 85-115µm and are designed
for high-performance microscopy applications.

To ensure that the porous membrane is positioned as close as possible to
the microscope objectives, whose working distance typically ranges
between 200μm and 1000μm, it is crucial that the channel is sufficiently
thin. To this end, we fabricated the bottom layer with a thickness of
100μm. This thickness provides adequate structural support for manual
handling, while avoiding potential microfluidic issues arising from
pressure loss and lower flow rates. To achieve the desired thickness, we
utilized a spin coating method to fabricate a thin layer of
polydimethylsiloxane (PDMS). Subsequently, the layer was precisely cut
into the channel shape using a desktop cutting machine (Silhouette Cameo
4, Silhouette America).

The primary function of the porous membrane is to enable pressure
application while preventing the migration of cells from the cell
channel to the pressure channel. Initially, we used a membrane with
pores of 10μm diameter based on literature. We attempted to create 10μm
pores in a 100μm thin layer of PDMS using photolithography to facilitate
manual handling. However, we encountered difficulty in fabricating 10μm
pillars with a height of 100μm due to an excessively high aspect ratio,
making the pillars too fragile and prone to breakage during fabrication
(see appendix B). Consequently, we opted to employ plastic, polyethylene
terephthalate (PET), membranes with 10μm pores.

The thin (10μm) plastic sheets were easily manageable, but we
encountered difficulties with bonding and experienced leakages due to
membrane wrinkling. To address these difficulties, we decided to modify
the middle layer by using a PDMS layer with a hole attached to a small
piece of membrane, instead of whole layer being a porous membrane. This
approach allowed us to achieve stronger and leak-proof bonding by
sandwiching a smaller area between the two PDMS layers. The middle PDMS
thin layer was constructed with a 1.2mm hole to expose the membrane to
pressure, as this dimension is approximately the size of the field of
view of a 10X objective.

The design of the top channel in the device involved a PDMS block with a
5mm thickness and a 1mm engraved channel. The decision to select the
thickness of the top channel was based on the requirement for the block
to be sufficiently thick to accommodate tubing for pressure application.
To create the mold with the channel, a precision 3D printer (Solus DLP
3D Printer) was utilized. Additionally, four inlets with a diameter of
1.5 microns were punched into the block using a biopsy punch to
facilitate two inlets for the pressure channel and two inlets for cell
seeding purposes (see fig 1.2).

Ultimately, the integration of the layers was accomplished through a
two-step bonding process utilizing an ozone plasma cleaner (refer to
Fig. 1.3). First, we bonded the glass to the bottom channel and
simultaneously bonded the middle layer to the top channel. Following
this step, the two assembled layers were bonded together with the
membrane sandwiched in the middle to create the final device.s

![ Fabrication of MOLI: Four layers assembled together with ozone plasma
cleaning. Each channels has a inlet and outlet. Only the pressure
channel is connected to the tubing; one side connects to the reservoir
and other is sealed. ](media/image30.png){width="5.2136887576552935in"
height="2.97829615048119in"}

***Fabrication of MOLI**: Four layers assembled together with ozone
plasma cleaning. Each channels has an inlet and outlet. Only the
pressure channel is connected to the tubing; one side connects to the
reservoir and other is sealed.*

### Protein patterning and \"upside-down\" cell culture

To overcome issues encountered in earlier prototypes, we opted to employ
a glass-bottomed dish (35 mm, no. 0 coverslip thickness, Cellvis) as the
container for our experimental setup. This design choice was made to
address concerns surrounding the potential for cell culture medium to
spill over/under the device during pressure application, especially in
the case of a leaky device.

In the context of the spontaneous dome system, the upper surface is
accessible for various treatments and microcontact printing using a PDMS
block. However, in our case, we have a completely sealed device, which
necessitated the use of the photopatterning technique known as PRIMO. In
brief, first the surface to be micropatterned is coated with
poly-L-lysine (PLL) and then SVA-PEG chains. Upon illumination with UV
light (375nm), PEG chains in selective regions could be cleaved and
subsequently exposed to adhesion-promoting proteins. The PRIMO technique
had been optimized previously for substrates made of glass and soft
PDMS. We had to optimize the technique for use with a porous plastic
membrane, which entailed increasing laser power to 1500mJ/mm^2^ (for
details see the Appendix A). We also optimized coating the devices with
fibronectin, vitronectin and collagen. For the experiments featured in
this thesis, we are using fibronectin mixed with fluorescent fibrinogen
for finding the samples.

To ensure successful attachment of cells and formation of monolayer, a
concentration of 25-30×10^6^ cells/ml was seeded for one hour, followed
by rigorous flushing with fresh cell culture media to wash away any
unattached cells. Early experiments revealed that while cells attached
to the top side of the porous membrane, there were very few dome
formations upon application of pressure. Additionally, imaging through
the porous membrane was poor quality, as the cells were further away
from the microscope objective, and some cells were filtering through the
membrane from top to bottom (see fig. 1.4).

![ Cells filtering through the membrane: (A) Images of MDCK-CiBN CAAX
GFP monolayer on the both sides of the membrane. Scale bar is 80\\mu m
(B) Schematic of imaging through the porous layer.
](media/image31.png){width="6.125in" height="2.079128390201225in"}

***Cells filtering through the membrane**: (A) Images of MDCK-CiBN CAAX
GFP monolayer on the both sides of the membrane. Scale bar is* $80\mu m$
*(B) Schematic of imaging through the porous layer.*

To prevent cells from crossing the membrane, various plastic membranes
with smaller pore sizes (ranging from 50 nm to 10 µm) were
systematically tested. Considering the flow rates and cell filtration
through the membrane, a 400 nm pore size membrane was chosen. However,
imaging the green channel (488 nm) through these pores was impossible.
Therefore, an \"upside-down\" cell culture approach was implemented,
where the device was flipped immediately after seeding cells in the
bottom channel to ensure attachment on the membrane instead of the glass
(see fig. 1.5). Thorough washing of the channel was necessary to prevent
cell attachment to the glass, which would have obstructed the imaging of
the domes.

Despite the optimization efforts, achieving a complete coverage of the
non-adhesive regions with the cell monolayer remained a significant
challenge. To address this issue, the protein concentration in these
regions was increased to facilitate cell attachment at the designated
dome location. However, to ensure dome formation upon application of
pressure, cells were encouraged to attach weakly in these regions. This
approach ensured that cells with weak adhesion detached first upon
pressure application, resulting in the formation of the desired dome
structure.

![ Upside-down cell culture: Illustration of upside-down cell culture
and the experimental setup on the microscope stage.
](media/image32.png){width="6.125in" height="3.2993153980752408in"}

*\
**Upside-down cell culture**: Illustration of upside-down cell culture
and the experimental setup on the microscope stage.*

### Pressure control

For the application of external pressure, we selected hydrostatic
pressure as the method of choice. Previous studies had reported a
pressure requirement of approximately 100 Pa, equivalent to 1 cm of
water column, for the formation of a dome. Initially, pipette tips were
employed to apply pressure, but we observed that they were susceptible
to bubble formation and leaks. Consequently, we switched to using
Polytetrafluoroethylene tubing, which was connected to a 50 ml reservoir
(Falcon tube) to mitigate these issues (refer to Fig. 1.6). By adjusting
the height of the tube to match the air-liquid interface in the
reservoir with the device, zero pressure was exerted on the cell
monolayer. To apply pressure, we increased the height of the tube by 2
cm, resulting in the application of 200 Pa pressure to the monolayer,
leading to the delamination of cells and the formation of domes.

Nonetheless, we exercised caution regarding the potential occurrence of
cavitation or bubble formation within the cell channel. To avoid this we
subjected the media to a vacuum chamber for 30min prior to the
experiment to eliminate any nascent bubbles that may have developed over
time. During tubing insertion, however, the system posed a risk of
reintroducing bubbles into the system. To counter this issue, we
employed the two inlets for each channel to flush fresh media from the
reservoir, ensuring that no bubbles were present.

sTo control the pressure, we used an automatic translation stage (Zaber
High speed motorized linear stage) that could be programmed to lift the
reservoir. We measured the pressure by tracking the height of the stage
and the zero-pressure position. With this stage, we could apply pressure
in the range of $0 \rightarrow 1500Pa$, and we could even apply negative
pressure by setting it lower. For our experiments, we used the range of
$- 200 \rightarrow 1300Pa$.

![ Hydrostatic pressure application: The device is positioned on a
microscope stage and connected to a reservoir of media, which in turn is
attached to a translation stage. By increasing the difference between
the device and the air-liquid interface, we can measure and apply
hydrostatic pressure. ](media/image33.png){width="3.858096019247594in"
height="2.2604330708661418in"}

*\
**Hydrostatic pressure application**:*

*The device is positioned on a microscope stage and connected to a
reservoir of media, which in turn is attached to a translation stage. By
increasing the difference between the device and the air-liquid
interface, we can measure and apply hydrostatic pressure.*

### Imaging the epithelial domes

![ Epithelial dome: Representative confocal microscopy sections of domes
at 0 Pa and 200 Pa. Images in the XY plane represent the dome's maximum
projection, while images in the XZ plane represent a cross section at
the center plane. Three cells are highlighted with color to show the
stretching during the dome inflation. Scale bar is 20 \\mu m.
](media/image34.png){width="4.337227690288714in"
height="3.7479122922134733in"}

***Epithelial dome:***

*Representative confocal microscopy sections of domes at 0 Pa and 200
Pa. Images in the XY plane represent the dome's maximum projection,
while images in the XZ plane represent a cross section at the center
plane. Three cells are highlighted with color to show the stretching
during the dome inflation. Scale bar is* $20\mu m$*.*

Following extensive optimization of protein patterning, cell culture
conditions, and confocal microscopy techniques, we were able to generate
domes in accordance with the intended pattern and exert precise control
over the pressure required for their formation. To obtain images of the
dome, we utilized a spinning disk confocal microscope with a 40x
objective lens (NA 0.75), which allowed us to visualize the membrane
(CIBN CAAX GFP) and adhesion protein (Fibrinogsen) pattern in separate
channels ($488nm$ and $644nm$, respectively). By incorporating a labeled
adhesion protein, we were able to track the formation of the domes with
greater ease and accuracy.

We initially focused on characterizing the mechanics of spherical domes
at constant pressure to gain insights into epithelial behavior (see fig
1.7). Laplace\'s law was employed to calculate tension using pressure,
cell shape, and tissue curvature data, which we could easily monitor.
Unlike previous studies that did not control the pressure under the
dome, our experimental system allowed us to inflate and deflate the
domes in seconds. This forced us to monitor them by observing the base
of the dome where the monolayer would intermittently come in and out of
view.

Acquiring images of the dome stack in a confocal microscope required
three minutes using a step size of 0.5μm (exposure 500ms) and a height
of 100μm, which was slower than the rate at which we could deform the
dome by changing the pressure (see fig 1.7). To investigate the rheology
of the domes, it was necessary to monitor their dynamic response at
faster pressure rates and shorter timescales while measuring dome strain
and curvature. Since the dome possessed inherent symmetry, imaging the
mid-section of the structure provided all the geometric information
required.

Using the line scanning mode of a Zeiss Airy Scan Microscope, we imaged
a single line of pixels across the midsection of the dome and acquired a
confocal z-stack (1024 pixel, 4.1µs/pixel dwell time, and 1µm step size)
along the height of the dome (refer to fig 1.8). This approach allowed
us to obtain a cross-sectional view of the dome in a fraction of the
time required for a normal stack. By enabling piezo stage movement, we
imaged a 100μm tall dome in just 4 seconds and tracked its height
evolution using a kymograph of the central part of the dome. It is
important to note that this imaging method is primarily useful for
tracking dome strain and curvature, and the cell images obtained are
often of low quality.

![ Imaging the dome with Line scanning mode: (A) Confocal microscopy
image of a dome's maximum projection. (B) Midsection of the same dome
imaged with the line scan mode (LSM). (C-D) Timelapse of the dome in LSM
and a kymograph showing dynamics of the domes when imaged at time-step
of 4s. Scale bars are 20 \\mu m.
](media/image35.png){width="4.500834426946632in"
height="4.1903171478565175in"}

*\
**Imaging the dome with Line scanning mode:***

*(A) Confocal microscopy image of a dome's maximum projection. (B)
Midsection of the same dome imaged with the line scan mode (LSM). (C-D)
Timelapse of the dome in LSM and a kymograph showing dynamics of the
domes when imaged at time-step of* $4s$*. Scale bars are* $20\mu m$*.*

### Light-sheet MOLI

![ Light sheet MOLI: (A) Isometric illustration of a single piece PDMS
block engraved with two channels, so that we can have two devices in
one. (B) Cross-section of the device. (C) The device is used with 40x
immersion objectives coming at 45 \\deg angle. This limits to the field
of view to 332\\times 332\\mu m\^2. ](media/image36.png){width="6.125in"
height="2.304882983377078in"}

***Light sheet MOLI**: (A) Isometric illustration of a single piece PDMS
block engraved with two channels, so that we can have two devices in
one. (B) Cross-section of the device. (C) The device is used with 40x
immersion objectives coming at* $45deg$ *angle. This limits to the field
of view to* $332 \times 332\mu m^{2}$*.*

We utilized a Brucker QuVi SPIM light sheet microscope to capture rapid
subcellular or cellular changes. The microscope was equipped with two
immersion-upright 40x objectives (NA 0.8) at 45 degrees to the
horizontal plane. Drawing upon our proficiency in device fabrication, we
devised a new setup that facilitated top imaging of cells and porous
membranes (refer to fig 1.9).

![ Dome imaged with Light sheet MOLI: Mid-section of a dome with
membrane marker imaged every 2s. Showing the shape of individual cells
undergoing changes during deflation. Scale bar is 20 \\mu m.
](media/image37.png){width="6.125in" height="1.4423436132983376in"}

**Dome imaged with Light sheet MOLI**: Mid-section of a dome with
membrane marker imaged every $2s$. Showing the shape of individual cells
undergoing changes during deflation. Scale bar is $20\mu m$.

To simplify the fabrication process, we inverted the conventional MOLI
device. This necessitated only a pressure channel and a middle layer
with a hole and porous membrane. The device was manufactured
sufficiently thick to plug in the tubing, and given the device and
channels\' size, we produced the mold using a standard 3D printer,
Ultimaker 3D printer. We incorporated a ridge-like protrusion to
manufacture the pressure channel and cell seeding hole in one go. The
device was bonded to a microscope slide using unpolymerized PDMS, and we
performed PRIMO patterning of the device by flipping it upside down. In
this setup, seeding cells was easier, as the cell seeding part was
exposed.

As expected, we were able to generate domes using the same system as
before by applying pressure. The imaging technique we developed enabled
us to acquire a full dome image in a mere 4 seconds, which involves
using objective scan, where only one objective to scan the dome with 100
frames with step size of 1µm at rate of 4ms. This allows us to observe
fast-moving features that were indiscernible with other imaging
techniques (refer to fig 1.10).

### Summary and Discussion

We have developed a microfluidic chip to generate 3D curved epithelia,
utilizing a multilevel device consisting of two layers separated by a
porous membrane. Seeding cells on the membrane in the bottom channel
allowed for dome formation closer to the microscope objective, enabling
high-quality confocal imaging. Hydrostatic pressure was used to control
pressure under the dome dynamically, allowing for monitoring of cells
and tissue behavior. Additionally, we developed imaging strategies to
capture dynamics of these 3D structures faster using line scanning mode
of confocal microscope or light sheet microscope.

It is important to acknowledge that while the method of forming 3D
epithelia described here may seem straightforward, it required numerous
iterations of the device and other attempted methods that ultimately
failed.

Nevertheless, we were able to form the domes and monitor cellular and
tissue behavior. As demonstrated in previous studies, the most
intriguing aspect of the system is that complex materials such as
epithelial tissue, in order to maintain mechanical equilibrium, must
adopt a spherical cap shape for a circular footprint. This uniform
curvature and pressure imply uniform tension, independent of tissue
material properties (Latorre et al., 2018; Marín-Llauradó et al., 2022).
The tissue tension can be easily measured by applying Laplace\'s law for
spherical cap domes. However, in the case of non-spherical geometry,
there would be anisotropic stresses that would require a computational
model, such as curved monolayer stress microscopy, to solve an inverse
problem to go from geometry to forces (Marín-Llauradó et al., 2022).

The geometry of the domes is primarily controlled by the adhesion
protein pattern, but delamination can still occur. In spontaneous domes,
circular footprints were found to be the most common (Tanner, Frambach,
and Misfeldt 1983), while domes formed around sharp corners can blunt
themselves through delamination (Latorre et sal. 2018). This must be
taken into consideration when creating specific geometries.

Tissue tension and adhesion forces also interact with each other. In
MDCK suspended monolayer, it is seen that cell-cell junctions are
stronger than cell-substrate adhesion (A. R. Harris et al. 2012), so if
tension at the base of the dome exceeds the adhesion forces, it can lead
to detachment and delamination.

Furthermore, we have unintentionally developed a peeling system that
enables us to observe tissue detachment from the substrate. If the dome
retains its spherical shape, we can calculate the necessary forces for
breaking cell-substrate adhesion and identify the contribution of focal
adhesion molecular components.

This system provides a novel approach for testing material properties
and probing mechanics at the tissue scale, allowing for simultaneous
high-quality imaging and monitoring of cytoskeletal components and the
nucleus. Additionally, we can create a 3D tissue with controlled lumen
pressure, providing a well-controlled protocol that is suitable for
replicating curvature-pressure-tension conditions in various cell lines,
not just MDCK cells. However, our primary focus is on comprehending the
mechanics of epithelial tissue under controlled pressure.

## Dynamic material response of epithelial domes

### Introduction

The motivation of this thesis was twofold: firstly, to produce
three-dimensional epithelia with controlled pressure, and secondly, to
study the material response of the tissue to different regimes of
tension. To achieve the first objective, we have developed a monolayer
inflator (MOLI) device that allows us to create epithelial domes where
cells can be stretched to more than $100\%$ of areal strain.

Epithelial tissue plays a crucial role in various physiological
functions, and must therefore undergo deformation over a wide range of
timescales and magnitudes. Similarly, pressure levels also vary widely
in different contexts (Torres-Sánchez, Kerr Winter, and Salbreux 2021;
Choudhury, Benson, and Sun 2022). For instance, the luminal pressure in
blastocysts doubles over the course of its development, resulting in
changes in cortical tension and strain (Chii Jou Chan et al. 2019). The
MDCK dome system provides a suitable platform to investigate the
interplay between cell strain, tension, and pressure. Previous studies
by Latorre et al. have observed a wide range of pressure throughout the
evolution of the dome, and cells have exhibited a range of deformation,
including active-superelastic behavior (Latorre et al. 2018). However,
the control in this system is limited to the footprint of the domes. In
this chapter, we aim to utilize the MOLI system to subject tissues to a
range of strain and tension regimes.

### Measurement of dome mechanics

[]{#fig_7_1 .anchor}![ Spherical cap: Here is an example of an
epithelial dome at 200 Pa, which has increased its surface area four
times the original footprint. One can clearly appreciate the beautiful
spherical shape of the dome in the cross-section. Scale bar is 20 \\mu
m. ](media/image38.png){width="5.2103499562554685in"
height="2.9582633420822395in"}

*\
**Spherical cap**:*

*An example of an epithelial dome at 200 Pa, which has increased its
surface area almost four times the original footprint. The spherical
shape of the dome can be seen in the cross-section. Scale bar is*
$20\mu m$*.*

To measure the kinematics of the domes, we analyzed the midsection of
the domes, assuming symmetry of spherical caps (see fig
[2.1](#fig_7_1)). We measured the height ($h$) and base radius ($a$).
This allowed us to calculate the radius of curvature ($R$) using
trigonometry as

$$R = \frac{h^{2} + a^{2}}{2h}.$$

The measurement of pressure ($\Delta P$) allowed us to compute the
tension ($\sigma$), given by Laplace's law

$$\sigma = \frac{\Delta PR}{2}.$$

For the dome strain, we used the areal strain measure, which is computed
based on the surface area. We compared the dome surface area ($A$) to
the area of the footprint ($A_{0}$).

$$\epsilon = \frac{A - A_{0}}{A_{0}} = \frac{\pi\left( h^{2} + a^{2} \right) - \pi a^{2}}{\pi a^{2}} = \frac{h^{2}}{a^{2}}.$$

By utilizing the line scanning modality of a Zeiss Airy Scan Microscope,
we were able to quickly obtain a significant number of frames for the
analysis of height and radius of curvature of the domes. To this end, we
generated kymographs by creating cross-sectional images of the top
section of the domes with respect to time. The kymographs were processed
using MATLAB-based image analysis code to determine the time evolution
of the dome height and base radius. Specifically, the location of the
maximum intensity value for a given time point in the graph was used to
track the time-dependent height of the dome, while the same approach was
utilized to obtain the time-dependent base radius. Importantly, he
kymograph of the base radius allowed us to keep track of delamination,
as it could change the value of strain.

### Epithelial domes at constant pressure

[]{#fig_7_3 .anchor}![Epithelial domes at constant pressure:Dynamic
response of the representative domes at a constant pressure of 200 Pa:
(A) Areal strain increases and reaches a steady state at around 5
minutes, and we can clearly see variability in the maximum strains. (B)
The same domes produce a peculiar \"NIKE swish\" shaped tension and
strain curve. ](media/image39.png){width="6.125in"
height="2.321188757655293in"}

***Epithelial domes at constant pressure**: Dynamic response of the
representative domes at a constant pressure of 200 Pa: (A) Areal strain
increases and reaches a steady state at around 5 minutes, and we can
clearly see variability in the maximum strains. (B) The same domes
produce a peculiar \"NIKE swish\" shaped tension and strain curve.*

Initially, our focus was to investigate the behavior of domes under
constant pressure. We systematically inflated domes at varying pressures
ranging from 0-400Pa, but observed that hardly any of the domes formed
at pressures lower than $50 - 100Pa$, Thus, we settled on using $200Pa$
which allowed domes to form without delaminating out of pattern.

Our measurements show that the areal strain of the dome increases during
the first three to five minutes of pressure application, and then
reaches a plateau in strain until $5 - 10$ minutes (see fig
[2.2](#fig_7_3) A). Despite large dome-to-dome variability, with strains
ranging from $50\%$ to $300\%$, the stabilization in strain suggests
that a steady state has been achieved by the tissue.

Upon further investigation of the tension-strain relationship exhibited
by these domes, a distinct curve was observed, bearing resemblance to
the swish symbol of \"Nike\" (refer to Fig. 2.2 B). The tension within
the domes was found to be extremely high for low strains, followed by a
decrease to a minimum value at an areal strain of one, where the dome
assumes a perfect hemispherical shape. Subsequently, the tension
increases once again, albeit with a slope that is comparably gentle in
comparison to the steep decline observed at lower strains.

Such a material response is atypical for biaxially stretched materials.
However, in this case, the underlying cause of the curve can be
attributed to the geometric constraints imposed by the dome system and
force balance, as governed by Laplace\'s law. Since the tension within
the dome is intrinsically dependent on its radius of curvature, the
initial high value of the radius of curvature leads to a correspondingly
high tension that subsequently diminishes to a minimum upon assuming a
hemispherical shape (refer to Fig. 2.3). It is important to note that
the radius of curvature, areal strain, and tension are all
interconnected, such that the expression of the curve can be derived at
a constant pressure. Given that radius of curvature and areal strain are

$$R = \frac{h^{2} + a^{2}}{2h},\ \ \ \ \text{and}\ \ \ \ \epsilon = \frac{h^{2}}{a^{2}}.$$

By substituting areal strain ($\epsilon$) in the expression of radius of
curvature ($R$),

$$R = \frac{h^{2}/a^{2} + 1}{2h/a^{2}} = a\frac{\epsilon + 1}{\sqrt{\epsilon}}.$$

By substituting ($R$) in Laplace's law, we get the relation,

$$\frac{\sigma}{a} = \frac{\Delta P}{4}\left( \frac{\epsilon + 1}{\sqrt{\epsilon}} \right).$$

Normalizing the tension with the base radius results in all domes
collapsing onto one curve corresponding to a specific pressure. Thus, we
could call these tension-strain curves \"isobarics\".

We recognize that when the step pressure is applied, the dome suddenly
inflates and has to undergo non-steady state out-of-equilibrium
stresses. It is clear that this curve does not represent the
quasi-static constitutive relation of the epithelial tissue.

![Illustrative explanation for isobaric curve: Tension and strain are
related to each other through the geometric constraint of a spherical
cap. Here, the base radius (a) is constant, so the radius of curvature
is almost infinite for domes with very small strains (\<0.05). As the
strain increases, the radius of curvature decreases to a minimum
corresponding to the base radius. Then it continues to increase again.
](media/image40.png){width="6.125in" height="3.144034339457568in"}

***Illustrative explanation for isobaric curve**: Tension and strain are
related to each other through the geometric constraint of a spherical
cap. Here, the base radius (a) is constant, so the radius of curvature
is almost infinite for domes with very small strains (\<0.05). As the
strain increases, the radius of curvature decreases to a minimum
corresponding to the base radius. Then it continues to increase again.*

### Constitutive relation of epithelia

In order to derive the actual constitutive relation of a material, it is
preferable to apply strain or tension in a quasi-static manner. However,
in our experimental system, only pressure could be controlled.
Therefore, we employed pressure control to establish steady state
tension across a range of strains. Slowly increasing pressure was not a
practical approach for domes, as they do not delaminate at low
pressures. In the case where delamination did occur, the domes would
rapidly inflate, thus reaching steady state at higher strains.
Consequently, steady state tensions at lower strains would not be
accessible. To overcome this limitation, we devised experiments to
capture the steady state of the domes by deflating them.

Specifically, we applied a pressure of 200 Pa for 5 minutes until the
dome reached steady state. Subsequently, we reduced the pressure in
increments of 20 Pa and allowed the dome to reach steady state at each
step (refer to Fig. 2.4 A). This process was repeated until the dome was
completely deflated. In this way, we were able to capture tension-strain
curves at different isobarics as the dome passed through various states.

Ultimately, we obtained a constitutive relation that exhibits an initial
increase in tension with strain for lower strains. However, for larger
strains, the tension appears to plateau consistent with earlier studies
on MDCK domes (refer to Fig. 2.4 B). It is worth noting that the
variability in dome-to-dome tension is significant, and the tensions
recorded around 4.5 mN/m are of the same order of magnitude as those
reported in previous studies (Latorre et al., 2018; Marín-Llauradó et
al., 2022).

![Constitutive Relation of Epithelia: (A) We will set up experiments to
probe the steady state at different pressures. We will start from the
highest pressure, move along the isobaric line and achieve a steady
state, and then move down to the next isobaric line, and so on. (B) The
constitutive relation between dome strain and tissue tension was
experimentally obtained (n=12). The line and shaded area represent the
median and standard deviation, respectively, by binning 13 points in
each bin. ](media/image41.png){width="6.125in"
height="2.2756627296587926in"}

***Constitutive Relation of Epithelia**:* *(A) Experiments were set up
to investigate the steady state at various pressures. Starting from the
highest pressure, we moved along the isobaric line to attain steady
state, then proceeded to move down to the next isobaric line and
repeated the process. (B) The constitutive relation between dome strain
and tissue tension was experimentally obtained (n=12). The line and
shaded area correspond to the median and standard deviation,
respectively, after binning 13 points in each bin.*

Dynamics of the epithelia domes

To investigate the dynamic material response of the domes, cyclic
stretching experiments were conducted by subjecting the domes to a
triangular wave of pressure with a magnitude of 200 Pa at three distinct
timescales, as depicted in Figure 2.5. The selected timescales of 20s,
266s, and 2000s were based on a the existing literature on tissue
remodeling, specifically focusing on the work of T. Wyatt, Baum, and
Charras (2016), Khalilgharibi et al. (2019), and Casares et al. (2015).

Notably, these aforementioned studies demonstrate that stress relaxation
experiments of the tissue occur from tens of seconds to minute
timescales due to F actin remodeling and myosin-driven contractility.
Moreover, in some cases, even faster deformation, at timescales of a few
seconds, has been shown to have an impact on cell remodeling (ref). For
these experiments, the fastest cycle that could be probed here was
limited to 20s, due to the imaging speeds of the microscope used in our
experiments.

  ---------------------------- ---------- ------------------- -----------
                               Fast       Moderate            Slow

  Time period (s)              20         266                 2000

  Rates (Pa/s)                 20         1.5                 0.2
  ---------------------------- ---------- ------------------- -----------

![Dynamic response of Epithelia: (A) The XZ plane images and kymographs
of domes subjected to cyclic pressure between 0 to 200 Pa with rates of
20, 1.5, and 0.2 Pa/s The kymographs generated along the midsection of
the domes indicated by yellow dotted lines. These indicate the evolution
of height of the domes with respect to time. (B) The strain response of
domes to cyclic pressure with different rates. Magenta represents
pressure and red represents strain with respect to time. For A, B, n= 7
domes for 20 Pa/s, n = 8 for 1.5 Pa/s, and n = 7 for 0.2 Pa/s.
](media/image42.png){width="6.125in" height="4.717533902012248in"}

***Dynamic response of Epithelia:** (A) The XZ plane images and
kymographs of domes subjected to cyclic pressure between 0 to 200 Pa
with rates of 20, 1.5, and 0.2 Pa/s The kymographs generated along the
midsection of the domes indicated by yellow dotted lines. These indicate
the evolution of height of the domes with respect to time. (B) The
strain response of domes to cyclic pressure with different rates.
Magenta represents pressure and red represents strain with respect to
time. For A, B, n= 7 domes for 20 Pa/s, n = 8 for 1.5 Pa/s, and n = 7
for 0.2 Pa/s.*

In the case of the fastest cycles, the domes progressively stretched
more as the cycles progressed until they reached a steady state
oscillation. The experiment was conducted over a duration of 1200
seconds, equivalent to 60 cycles, wherein we observed a gradual increase
in the maximum strain in each cycle, as well as a cumulative buildup of
strain over time During the loading phase, the domes underwent
stretching, while during the unloading phase, they experienced an
unstretching effect, albeit failing to revert to zero strain after the
initial cycles. In the concluding cycles, we noted that the dome
oscillated between two distinct states of strain, resembling a limit
cycle.

A similar response was observed for the moderate cycles, where the domes
were stretched for five cycles of $266s$ each. The strain accumulated in
the first cycle itself, with strains reaching higher values than those
observed in the fast case. Additionally, after a few cycles, the dome
appeared to have reached a stable limit cycle.

For the slowest cycles, two spanning a duration of 4000 seconds, we
observed that the domes did not form at lower pressures. As previously
discussed, the domes remained attached until a pressure of 100-150Pa was
attained, beyond which they underwent rapid inflation, leading to high
strains of 200-350%. However, in cyclic stretching, we noted that strain
accumulation did not occur, and there was no variation in the maximum
strains attained during both cycles, indicating stable oscillations all
throughout the cycles.

### Active gel tissue model

We closely collaborated with Adam Ouzeri to develop a computational
framework that incorporated the phenomenologies observed in our
experiments. The existing literature on epithelial mechanics highlights
the crucial role played by the viscoelasticity of the actin cortex in
sustaining deformations over timescales spanning seconds to minutes
(Kelkar, Bohec, and Charras 2020; Clément et al. 2017; Khalilgharibi et
al. 2019). The theoretical framework developed herein serves as a bridge
between active gel models of the actomyosin cortex and 3D vertex models
at tissue scales (Ouzeri and Arroyo 2023). In this model, each cell is
represented by an active gel surface that accounts for the physical
attributes of the cortex, while a tissue is constructed from a
collection of these active gel surfaces (as depicted in Fig 2.6). The
system\'s dynamics are formulated through a balance of diverse
potentials representing various active internal or external forces and
dissipation.

**Box**: Model summary

The actin filament network is modeled as a hyperelastic membrane with a
specific cortical thickness. As the cortex undergoes stretching, we must
consider its deformation through **network elasticity** (λ). However,
since the network relaxes due to turnover or contractility, we add a
dissipative potential to account for the released elastic energy. This
relaxation can be equated to viscous behavior, which can be represented
by a **viscosity coefficient** (η) in the model. To model active
contractility, we incorporate an active power potential generated by the
**active tension** (ξ) of the cortex.

It is crucial to note that certain assumptions are made in the model:
firstly, the volume of the cell is conserved; secondly, active tension
is proportional to cortical thickness; thirdly, there is a steady-state
cortical thickness, and the network is continually **turning over**
(k~d~); Lastly, to limit the strains, there is a strain stiffening
mechanism which gets activated at high strains.

Turnover time ($t_{to} = 1/k_{d}$)

Viscoelastic time ($t_{ve} = \eta/\lambda$)

Viscoactive time ($t_{va} = \eta/\xi$).

The framework accounts for the molecular dynamics of the actin filament
network, myosin, and crosslinker proteins through four main components:

1.  **Cortical thickness:** The cell cortex is modeled as a hyperelastic
    membrane with cortical thickness ($\rho_{R}$). The deformation
    kinematics of this model is defined by mapping a cortical patch from
    a reference configuration ($\Gamma_{0}$) to a deformed configuration
    ($\Gamma$) with metric tensor [^11] ($\mathbf{G}_{\mathbf{0}}$) to
    ($\mathbf{g}$), respectively. To capture remodeling of cortex, the
    reference configuration must be dynamic as well. Thus, there is a
    second reference configuration with a dynamic metric tensor
    ($\mathbf{G}$). The cortical thickness in the reference
    configuration changes with the mapping change represented by the
    Jacobian ($J_{R}$). This is expressed as

$$\rho_{R}\left( \mathbf{\xi},t \right) = \rho(x,t)J_{R}\left( \mathbf{\xi},t \right).$$

2.  **Network elasticity:** This potential accounts for the free energy
    of the system undergoing deformation. The potential is dependent on
    the difference between in-plane strain ($\mathbf{C}$) and the metric
    ($\mathbf{G}$) written in the format of a hyperelastic potential
    ($W$). Using a Neo-Hookean elastic potential, $W$ depends on two
    Lamé parameters, ($\lambda$) and ($\mu$). This potential is
    expressed as

$$\mathcal{F =}\int_{\Gamma_{R}}^{}\rho_{R}\ W\left( \mathbf{C,G} \right)dS_{R}.$$

3.  **Dissipation:** The actomyosin network remodels under tension, and
    the released elastic energy can be accounted for with a dissipation
    potential. The potential depends on a coefficient ($\eta$)
    equivalent to bulk viscosity, cortical thickness, and the rate of
    metric tensor given by ($\dot{\mathbf{G}}$). This potential is
    expressed as

$$\mathcal{D =}\int_{\Gamma_{R}}^{}\frac{\eta}{2}\ \rho_{R}\ \dot{\mathbf{G}}:\dot{\mathbf{G}}\ dS_{R}.$$

4.  **Active contractility:** The model is an active gel, and the active
    part is included through an active power potential that adds energy
    to the system. The potential is dependent on the cortical tension
    and the rate of deformation tensor. The cortical tension is an
    active tension component of the network that is proportional to
    cortical thickness. This potential is expressed as
    $\gamma(\rho) = \rho\xi$ and

$$\mathcal{P =}\int_{\Gamma}^{}\gamma:\mathbf{d}\ dS.$$

Additionally, we account for turnover dynamics in the cortex through a
mass balance law. Here, we assume that there is a steady-state cortical
thickness, and the network is constantly polymerizing and depolymerizing
with cytosolic components. This is expressed as

$$\dot{\rho} + \rho\ tr\left( \mathbf{d} \right) = k_{p}\ C - k_{d}\ \rho.$$

The proposed governing equations are obtained by minimizing the
Rayleighian, which is given as:

$$\mathcal{R =}\frac{dF}{dt} - D + P + P_{e}.$$

Here, $P_{e}$ is an additional potential that accounts for external
forces and tractions. The model assumes that the volume of the cell is
conserved during deformation, and a mechanical barrier is introduced to
prevent excessive strains beyond a threshold. This barrier is
implemented by adding re-stiffening at large strains, which is necessary
for physiological reasons, such as reorganization of intermediate
filaments, cell crowding, or compression of the nucleus.

[]{#fig_7_2 .anchor}![Active gel tissue model: (A) The cell is modeled
as an active gel of cortex, which mainly comprises three aspects:
viscoelasticity of the network, turnover dynamics, and active
contractility. (B) These cells can be assembled into a tissue that can
be used to perform in-silico experiments. An example of this is the
digital dome being inflated, highlighting individual cells increasing
their area.](media/image43.png){width="5.676126421697288in"
height="2.407344706911636in"}

***Active gel tissue model**: (A) The cell is modeled as an active gel
of cortex, which mainly comprises three aspects: viscoelasticity of the
network, turnover dynamics, and active contractility. (B) These cells
can be assembled into a tissue that can be used to perform in-silico
experiments. An example of this is the digital dome being inflated,
highlighting individual cells increasing their area.*

The model exhibits three timescales: turnover time ($t_{to} = 1/k_{d}$),
viscoelastic time ($t_{ve} = \eta/\lambda$), and viscoactive time
($t_{va} = \eta/\xi$). At shorter timescales, the system behaves like an
active hyperelastic material, while at longer timescales, it behaves
like an active viscoelastic material.

The model was implemented to study dome system by creating a digital
equivalent of the monolayer consisting of cell membranes. Non-adhesive
regions were also included, which could be inflated into domes under
pressure, similar to the experimental setup. Here after, we will refer
to them as \"digital domes\" (see fig. [2.6](#fig_7_2)).

### Active viscoelasticity of the epithelia

[]{#fig_7_7 .anchor}![Material response of the digital domes: (A) When
subjected to constant pressure, as in experiments, the digital dome
inflated and reached a steady state. (B) These simulations also produced
isobarics for different pressures, all leading to a steady state.
Furthermore, subjecting it to a quasi-static increase in pressure
produced a constitutive law (Navy blue curve) that can be mapped onto
the locus of steady-state
points.](media/image44.png){width="6.0617694663167105in"
height="3.0617694663167105in"}

***Material response of the digital domes**: (A) When subjected to
constant pressure, as in experiments, the digital dome inflated and
reached a steady state. (B) These simulations also produced isobarics
for different pressures, all leading to a steady state. Furthermore,
subjecting it to a quasi-static increase in pressure produced a
constitutive law (Navy blue curve) that can be mapped onto the locus of
steady-state points.*

By conducting simulations that mirror the experimental conditions, we
found that when digital domes were inflated with constant pressure, they
reached a steady state while experiencing a reduction in cortical
thickness as the cells stretched. Once the tissue tension was balanced
by the applied pressure, the strain reached a stable point (see fig
[2.7](#fig_7_7) A).

To obtain the constitutive relation, we inflated the digital dome with
different pressures to obtain isobaric curves and steady state point. We
also inflated a digital dome quasi-statically to assess the model's
robustness. We discovered that the constitutive relation obtained
quasi-statically was consistent with the steady state locus in the
isobarics (see fig [2.7](#fig_7_7) B). The constitutive curve exhibits
similar characteristics to experiments, including clear re-stiffening at
large strains, which we attribute to a barrier mechanism.

We interpreted these findings by using the concept of resting area,
which refers to the area of a cell in a monolayer that is in a steady
state. In the model, it is given by the metric tensor of dynamic
reference configuration:

$$A_{rest} = \ \ \ \int_{\Gamma_{0}}^{\ }\sqrt{\left| \mathbf{G} \right|}dS_{0}\ ,$$

And actual area is

$$A_{actual} = \ \ \ \int_{\Gamma}^{\ }{dS}\ .$$

When the tissue is perturbed from this state, the actual area can change
faster than the resting area due to the viscoelastic behavior of the
tissue. The cell dissipates elastic stresses at viscoelastic timescales
through remodeling, eventually reaching a steady state. This effect of
timescales is particularly evident in cyclic stretching experiments.
When the cells are probed faster than viscoelastic timescales, they
accumulate strains due to an inability to dissipate the elastic stress.
In contrast, when stretching is slower, elastic stresses are dissipated
with increasing area.

We observed that, for the slowest condition, the resting area in the
digital dome almost overlapped with the actual area. This is because the
pressure is changing very slowly at a rate of 0.2 Pa/s, allowing the
cells sufficient time to remodel and dissipate elastic stresses.
Viscoelastic and turnover timescales in simulations are around 10-30s,
which means that over a period of 2000s, the dome stretches considerably
and returns to original flat state.

However, when pressure is applied rapidly in cycles of 20 seconds,
strains accumulate due to insufficient time for cells to dissipate
stored elastic energy. The simulations show that the resting area
marginally changes relative to the actual area. Notably, creep
experiments, where tissue is stretched at constant tension, demonstrate
strain accumulation at the visco-active timescale, where both
contractility and viscosity play a role.

Interestingly, the simulations indicate that due to active
viscoelasticity, there would be a lag between the peak of pressure and
the peak of strain. This lag is clearly reflected in the comparison of
resting area and actual area, where the delay decreases with increasing
pressure rates. The slowest pressure rate results in the least amount of
delay, while the fastest pressure rate results in the most delay.
Although we can only experimentally observe this at moderate rates. The
experimental data from faster cycles is too noisy to observe the lag.

To sum up, the digital dome model explains the material response of
epithelial tissue depending on the rate at which pressure is applied.
Slower rates allow for cell remodeling and dissipation of elastic
stresses, while faster rates result in strain accumulation due to
insufficient time for dissipation. This active viscoelastic behavior is
the outcome of cortical remodeling.

![Concept of resting area: (A) Illustration of a resting and actual are
of a cell in a monolayer during stretching. (B) Differences in results
of resting and actual area when subjected to different rates of
pressure. (C) Inset of the last two cycles.
](media/image45.png){width="6.125in" height="5.965875984251968in"}

***Concept of resting area**: (A) Illustration of a resting and actual
are of a cell in a monolayer during stretching. (B) Differences in
results of resting and actual area when subjected to different rates of
pressure. (C) Inset of the last two cycles.*

### Summary and Discussion

In this chapter, we investigated the mechanics of epithelial tissue by
applying pressure at varying rates. Initially, we applied a constant
pressure of $200Pa$, which led to the dynamic inflation of domes and
eventually reached a steady-state in strain. Due to the spherical
geometry of the tissue, we observed a non-monotonous tension-strain
curve in response to the constant pressure. However, we found that the
true tension-strain curve exhibited increasing tension with respect to
strains at lower values, but at higher strains, the tension appeared to
be independent of the strains.

Furthermore, our measurements showed that the domes accumulated strain
through the cycles when probed with fast-changing pressure and reached a
steady-state in later cycles. However, when stretched slowly, the domes
stretched to higher strains without accumulating strain at the end of
the cycle.

To understand the behavior of epithelial tissue, we developed
computational framework, which show that the response of the domes to
cyclic pressure is dependent on active viscoelasticity.

The tissue stretches to balance the tissue tension with externally
applied pressure timescale and reaches a steady-state strain by actively
remodeling the cortex. Our digital dome studies indicated that different
timescales play a role together in producing the tissue's response to
pressure. These timescales are the reflection of interplay between
cortical turnover, crosslinkers, and network reorganization which allows
for large deformations and rapid shape changes.

Our results can be interpreted using a multidimensional Maxwell model,
which is a model that describes viscoelasticity. The classical Maxwell
model consists of a spring and a dashpot, which represent the elastic
and viscous elements, respectively. In our case, we can imagine a
similar model with two branches: one branch includes a spring and a
dashpot to represent the passive viscoelasticity, and a second branch
includes an active spring to represent the active component (see fig
[2.9](#fig_7_9)). The active spring is always present, but if the
stretching is done slowly, the dashpot would be driving the dominant
mechanical response. Conversely, if the stretching is done rapidly, the
elastic spring deformation would dominate. By separating the passive and
active components, we can better understand how each contributes to the
overall viscoelastic behavior and associated timescales.

[]{#fig_7_9 .anchor}![Representational viscoelasticity model: The model
can be understood using a spring and dashpot analogy with two branches:
The first branch is an active spring representing the contractile forces
applied by the actomyosin cortex. The second branch has two components,
one for the elasticity of the network and the second for the viscous
relaxation that occurs due to turnover of the network.
](media/image46.png){width="5.400667104111986in"
height="2.3071784776902886in"}

***Representational viscoelasticity model**: The model can be understood
using a spring and dashpot analogy with two branches: The first branch
is an active spring representing the contractile forces applied by the
actomyosin cortex. The second branch has two components, one for the
elasticity of the network and the second for the viscous relaxation that
occurs due to turnover of the network.*

Previous research has approached the system in a similar manner, where
epithelial tissue was modeled using viscoelastic models of springs and
dashpots. One particularly interesting model was developed by
Khalilgharibi et. al., which characterizes the response of a suspended
monolayer to stretch and demonstrates that the dynamics are similar to
that of a single cell, due to the role of the actomyosin cortex
(Khalilgharibi et al. 2019). They used a model with two springs in
parallel, one of which can change its resting length dynamically. This
explains the relaxation of the monolayer, where the active contractility
of the cortex changes the resting length of the active spring in the
model, which closely relates to our \"resting area\" concept.

Another study found that viscoelastic dissipation could explain the
shortening or elongation of cell junctions in drosophila embryos
(Clément et al. 2017). They demonstrated that the dissipation occurs at
the minute timescale, at the same timescale as myosin pulses. It is also
interesting that they found actin turnover plays a key role in this
dissipation.

Applying tensions and strains to suspended cells in vitro is a
challenging task, and it is important to note that adherent monolayers
may exhibit different behaviors from suspended cells (A. R. Harris et
al. 2012). The tissue matrix provides additional stiffness and can alter
the cytoskeletal structure of cells, which further complicates the
understanding of cell mechanics (Humphrey, Dufresne, and Schwartz 2014;
Kechagia, Ivaska, and Roca-Cusachs 2019). In this thesis, we focused on
probing the response of suspended tissues at the short timescales
(minutes), which is the timescale of acto-myosin network remodeling.

We did not observe any cellular rearrangement, extrusion, or division at
this timescale in our system (with rare exceptions). Long-term
experiments were not performed due to suspected involvement of other
cytoskeletal components, such as intermediate filaments. In a study by
Latorre et al., activation of intermediate filaments was observed in
extremely stretched cells ($> 300\%$), where they proposed that this is
caused re-stiffening and prevented the cells from stretching too much
(Latorre et al. 2018). This motivated the strain limiting mechanism
imposed in our model. However, in our experiments, we did not observe
any indication of superelasticity, as all cells were super-stretched at
the same time. This might be due to the relatively shorter timescales in
our experiments compared to long term quasi-static deformation of
spontaneous domes.

**About strain stiffning and results of (Duque et al. 2023). About
racheting of contractile force (Clément et al. 2017; Mason and Martin
2011) and strain accumulations or creep**

In the next chapter, we will endeavor to apply our understanding of
viscoelasticity to generate radical transformation of domes into various
structures.

## Epithelial Buckling: Transforming Domes into Folds

### Introduction

Epithelial structures in biology exhibit a diverse range of shapes and
sizes, including curved or folded forms. Understanding these structures
can be complicated, particularly in the context of developmental
biology. Interestingly, the etymology of the terms \"development\" and
\"complicated\" provides insight into the importance of folding and
unfolding processes. \"Development\" comes from \"desvelopemens,\"
meaning \"unfolding,\" which describes the morphogenesis of an organism.
In contrast, \"complicated\" comes from \"com-plicare,\" meaning
\"folded together,\" which is fitting for describing the emergence of
complex, folded structures in epithelial tissues.

By utilizing the MOLI tool, we can create 3D epithelial structures by
inflating domes, thereby transforming a planar monolayer into a curved
configuration. In this chapter, we will discuss how these structures can
be made even more \"complicated\". By studying the mechanics of
epithelial tissue, we have discovered that the dome can be deflated into
folds by rapidly depressurizing it. We will explore the process of
epithelial buckling and discuss how this knowledge has enabled us to
transform domes into folded structures.

### Rapid deflation produces a buckling instability

[]{#fig_8_1 .anchor}![Digital dome undergoing buckling:Here, a digital
dome at a steady state is rapidly deflated to a negative pressure of
-50Pa. As the cells don't have enough time to reduce their area, they
collapse into a fold. ](media/image47.png){width="6.125in"
height="1.70832239720035in"}

***Digital dome undergoing buckling**: Here, a digital dome at a steady
state is rapidly deflated to a negative pressure of* $- 50Pa$*. As the
cells don't have enough time to reduce their area, they collapse into a
fold.*

In the preceding chapter, we observed that the domes exposed to a
constant pressure would gradually inflate and eventually reach a steady
state, which can be attributed cytoskeletal remodeling. Specifically,
the original footprint area increased to areal strains exceeding
$100\%$, more than double the original area. Moreover, when subjected to
cyclic stretching, we observed that rapid inflation-deflation cycles
accumulated strains in the tissue. Given the precise control over
pressure, we decided to expose the tissue to extreme rates of pressure,
allowing no time for relaxation and leading to buckling instability.

By using the computational model, we were able to examine the mechanical
effects of deflation on the digital dome at both tissue and cell scales.
Our analysis revealed that active viscoelastic dissipation through
cortical remodeling allowed the dome to achieve high strains. When we
subjected the dome to cyclic stretching at rapid rates, we noticed a
discrepancy between the actual and resting areas. This observation
suggested that fast deflation could induce negative viscoelastic stress
greater than active tensions, leading to buckling.

Our findings showed that digital domes gradually returned to a flat
monolayer when deflated at a rate slower than the remodeling timescale.
However, deflating the domes more quickly than the remodeling timescales
resulted in buckling (see fig [3.1](#fig_8_1)). Simulations revealed
that the negative pressure was necessary for inducing buckling, which
affected only rapidly deflating domes. This was due to negative
stresses, as the pressure became negative while the curvature remained
positive. In contrast, slowly deflating domes reached zero strain as the
pressure approached zero.

To systematically test our hypothesis regarding the factors affecting
buckling events, we designed experiments with pressure profiles
consisting of three stages (see fig [3.2](#fig_8_2)). Firstly, we
initiated a linear increase in pressure from 0 to 200 Pa over a period
of 10 seconds. Secondly, we applied constant pressure for varying \"hold
times,\" which were chosen based on the timescales associated with
actomyosin cytoskeletal remodeling. Finally, we decreased the pressure
to -50Pa at varying \"deflation rates.\"

[]{#fig_8_2 .anchor}![ Buckling protocol: The pressure is increased to
200Pa for inflating the dome, and then the dome is given different
amounts of time (hold time) to remodel before being deflated to -50Pa at
different rates (deflation rate) to observe whether the dome buckles or
not. ](media/image48.png){width="3.9015015310586176in"
height="1.7646073928258967in"}

***Buckling protocol**:*

*The pressure is increased to 200Pa for inflating the dome, and then the
dome is given different amounts of time (hold time) to remodel before
being deflated to -50Pa at different rates (deflation rate) to observe
whether the dome buckles or not.*

It is important to note that we relied on qualitative characterization
of buckling events, assuming that smooth and continuous curvature of the
monolayer indicates the absence of buckling. We performed the
experiments for all conditions and quantified the data by tracking the
fraction of domes that underwent buckling.

Our results showed that buckling occurred for all hold times, ranging
from 6s to 600s, at the fastest deflation rate of 200 Pa/s. This
confirmed the hypothesis that rapid deflation would induce compressive
stresses and cause buckling (see fig [3.3](#fig_8_3) A-B). On the other
hand, slow deflation at a rate of 0.2 Pa/s rarely led to buckling,
regardless of the hold time (see fig [3.3](#fig_8_3) C-D). This suggests
that the tissue can effectively remodel its cytoskeleton and adapt to
drastic changes in area to avoid buckling.

As seen in previous experiments, longer \"hold times\" allowed for more
cytoskeletal remodeling, resulting in higher strains and a higher
likelihood of buckling, even for slower deflation rates. Results plotted
in a phase diagram illustrates the trend: as hold time increases,
buckling becomes more likely at faster deflation rates and less likely
at slower deflation rates with a shorter hold time (see fig
[3.3](#fig_8_3) E).

Interestingly, the data showed that domes with a 6s hold time had
smaller strains compared to those with a 600s hold time, which is
consistent with results from domes subjected to constant pressure (see
fig [3.3](#fig_8_3) F). Strain increase requires time for the dome to
remodel and balance active tension with the externally applied pressure.
Despite a hold time of 6 seconds, we still observed buckling within the
system. The expectation for this condition was to enable the inflation
and deflation of the dome before any cytoskeletal remodeling could
occur. We selected a 6-second hold time based on the imaging speeds;
however, the inflation and deflation process was still too slow for the
timescales of cytoskeletal remodeling.

It is important to note that we observed a wide variety of buckling
patterns when examining midsections of the tissue through a line scan
method. Some domes exhibited minor kinks in the folds, while others
showed drastic buckling modes similar to those of plates.

[]{#fig_8_3 .anchor}![Buckling conditions: (A-D) Representative montages
of dome deflation for experiments and model at different deflation rates
of 200 and 0.2 Pa/s after holding pressure constant of 200 Pa for 6 and
600 s. Scale bars are 20 µm for XZ. (E) Diagram representing fraction of
domes buckling for different deflation rates and hold time. Showing the
optimum conditions for the buckling. (F) The maximum strain achieved is
lower for 6s hold time compared to 600s conditions.
](media/image49.png){width="6.125in" height="6.014508967629046in"}

***Buckling conditions**: (A-D) Representative montages of dome
deflation for experiments and model at different deflation rates of 200
and 0.2 Pa/s after holding pressure constant of 200 Pa for 6 and 600 s.
Scale bars are 20 µm for XZ. (E) Diagram representing fraction of domes
buckling for different deflation rates and hold time. Showing the
optimum conditions for the buckling. (F) The maximum strain achieved is
lower for 6s hold time compared to 600s conditions.*

### Multiscale buckling

![Multiscale buckling: (A-C) Representative images of the domes
undergoing buckling at different scales. Buckled and unbuckled states of
the dome with zoom in section buckled component. Dotted yellow line
represents uniform curvature in unbuckled state and non-uniform
curvature in buckled state. Scale bar is 20 \\mu m. (B) Evolution of a
single cell in the dome during buckling. Highlighted by yellow arrow.
(C) Some parts of cells undergo buckling producing short wavelength
folds. (D) These folds are also present in the cortex too. Scale bar is
5 \\mu m for (B-D). ](media/image50.png){width="6.125in"
height="6.460557742782152in"}

***Multiscale buckling**: (A-C) Representative images of the domes
undergoing buckling at different scales. Buckled and unbuckled states of
the dome with zoom in section buckled component. Dotted yellow line
represents uniform curvature in unbuckled state and non-uniform
curvature in buckled state. Scale bar is* $20\mu m$*. (B) Evolution of a
single cell in the dome during buckling. Highlighted by yellow arrow.
(C) Some parts of cells undergo buckling producing short wavelength
folds. (D) These folds are also present in the cortex too. Scale bar is*
$5\mu m$ *for (B-D).*

The observation of tissue buckling was evident in the confocal line scan
images. In order to gain a clearer understanding of the shape of the
cells, we adapted a variation of MOLI for use with light sheet
microscopy. The higher resolution 3D images of the dome revealed a
variety of thicknesses of the cells, with thicker regions caused by the
bulging of the nucleus and very thin regions at the cell periphery (see
fig [3.5](#fig_8_6) B).

To further investigate the phenomenon of buckling, we repeated the
experiments described in the previous section, with rapid deflation and
a long hold time. We discovered additional features beyond tissue-scale
buckling, including kinks and crimps at cellular and subcellular scales.
Upon closer inspection, we classified three levels of buckling:

1.  Tissue

2.  Cellular

3.  Subcellular

At the tissue scale, buckling was visible with cells collectively
transitioning from a uniform curvature to a distorted shape (see fig
[3.5](#fig_8_6) A). At this level, we observed cell deformation at a
larger scale, including at the junctions between cells.

At shorter length scales, we observed individual cells undergoing
buckling (see fig [3.5](#fig_8_6) B). The buckling of the cell resulted
in the cell doubling up around itself, with the apical side at the top.
The length scale at which cell buckling occurred was much shorter than
that observed at the tissue level. It appears as though the cell buckles
as a single unit.

In some cases, buckling occurred at even shorter length scales, which we
refer to as subcellular buckling, as the folds in the membrane were
distinct from the cell level buckling. These folds occurred in the
thinnest parts of the stretched cells, where the membrane buckled at
much shorter wavelengths (see fig [3.5](#fig_8_6) C). Interestingly,
these folds occurred on both the apical and basal sides of the cells.

[]{#fig_8_6 .anchor}![Cell level buckling: In many instances where the
tissue does not buckle, we observe individual cells buckling. Here is an
example of cell buckling (A) and subcellular buckling
(B).](media/image51.png){width="5.316582458442695in"
height="3.452260498687664in"}

***Cell level buckling**: In many instances where the tissue does not
buckle, we observe individual cells buckling. Here is an example of cell
buckling (A) and subcellular buckling (B).*

In epithelial cells, the membrane is typically attached to the cortex
through membrane-cortex attachment proteins such as ezrin, radixin, and
moesin. It is reasonable to assume that the subcellular buckling
observed in our experiments is due to actin cortex buckling. To confirm
this, we imaged the actin cortex while the dome was undergoing buckling
using SPY actin staining (see fig [3.5](#fig_8_6) D). Our results showed
that the actin cortex followed the exact shape of the membrane during
buckling.

We also observed that some domes did not appear to be buckling at the
tissue scale, but were still exhibiting buckling at the cell or
subcellular level (see fig [3.8](#fig_8_7)). These categories are not
strictly separated, as we observed multiple instances of tissue, cell,
and subcellular level buckling (see fig [3.5](#fig_8_6) A).

### Generating epithelial folds

After optimizing the buckling conditions, we embarked on exploring
epithelial folds. We have been imaging only the cross-section of the
dome to capture the fast dynamics. We see the buckling in form of the
curvy lines. However, these buckling events are three-dimensional (see
fig [3.3](#fig_8_3) B). During tissue buckling, a large area squeezed
into original footprint area resulted in the formation of folds and
wrinkles in the monolayer. Monitoring the base of the dome deflating, we
observed that the tissue made contact with the substrate in certain
regions first and others later. This led to the formation of folds in
the regions where it made contact last (see fig [3.7](#fig_8_5) A-C).

To investigate if there was any pattern to these folds, we looked at
spherical domes of various sizes. Broadly, we observed two types of
folding patterns emerging (see fig [3.6](#fig_8_8)):

1.  Accumulation along the periphery

2.  Folds in the middle

[]{#fig_8_8 .anchor}![ Buckling patterns: Buckling patterns observed in
differently sized digital domes. The domes were grouped into three size
categories and two categories based on location of folds (along the
border and in the middle). We found that larger domes are more likely to
buckle into a network of folds compared to smaller ones.
](media/image52.png){width="2.2964818460192475in"
height="2.618089457567804in"}

***Buckling patterns**:*

*Buckling patterns observed in differently sized digital domes. The
domes were grouped into three size categories and two categories based
on location of folds (along the border and in the middle). We found that
larger domes are more likely to buckle into a network of folds compared
to smaller ones.*

For domes with a footprint diameter smaller than $\sim 110\mu m$, we
repeatedly observed that most of the buckling resulted in an
accumulation around the periphery (see fig [3.7](#fig_8_5) A). The
confocal timelapse from the base gave the impression of a donut-like
structure, but three-dimensional imaging of the folds revealed a
crescent-shaped fold like a croissant, taller on one side than the
other. For larger domes with a footprint diameter greater than
$\sim 300\mu m$, we observed more instances of domes forming a network
of folds in the middle, with multiple folds connecting each other by
forming junctions (see fig [3.7](#fig_8_5) C). Finally, for domes of
intermediate size, we observed a mixture of accumulation and folds,
although the proportion of folds along the periphery decreased (see fig
[3.6](#fig_8_8)).

Interestingly, we observed the same folding patterns in our digital
domes when performing the same deflation experiments (see fig
[3.7](#fig_8_5) D). Larger digital domes produced more radial folds, and
small digital domes formed an accumulation on the side.
Intermediate-sized digital domes showed a mixture of both patterns.

[]{#fig_8_5 .anchor}![Buckling patterns in spherical domes of varied
size: Representative examples of digital domes undergoing buckling with
time-lapse of their basal cross-section (A-C). In the first frame, the
onset of buckling is visible where the dome makes contact in the middle.
Subsequent frames show more of the fold coming into view, and when the
dome completely deflates, a fold is formed (indicated by the green
arrow). Panel (D) shows the final outcome of buckling for digital domes
of different sizes. Scale bar is 20 \\mu m
](media/image53.png){width="6.125in" height="5.775711942257218in"}

***Buckling patterns in spherical domes of varied size**: Representative
examples of digital domes undergoing buckling with time-lapse of their
basal cross-section (A-C). In the first frame, the onset of buckling is
visible where the dome makes contact in the middle. Subsequent frames
show more of the fold coming into view, and when the dome completely
deflates, a fold is formed (indicated by the green arrow). Panel (D)
shows the final outcome of buckling for digital domes of different
sizes. Scale bar is* $20\mu m$

### Forming predictable folds

[]{#fig_8_7 .anchor}We were intrigued by how variations in the geometry
of the domes might influence the pattern formation of folds. While we
observed that spherical domes of different sizes produced varying and
intricate buckling patterns, their axis-symmetric shape made it
challenging to predict the patterns accurately. To overcome this
limitation, we decided to generate large digital domes of the same
footprint area but with distinct geometries, including an ellipsoidal
and a triangular shape. Remarkably, we found that the digital domes
buckled into predictable patterns, with the ellipsoidal shape forming a
line along the major axis and the triangular shape forming a Y junction
fold.

In order to explore the effects of geometry on the formation of folds in
epithelial structures, we conducted experiments using MOLI with
ellipsoidal domes of varying sizes. Our observations revealed that
larger ellipsoidal domes would buckle into a fold along their major
axis, just as digital domes, while smaller ellipsoidal domes produced a
similar peripheral accumulation as spherical domes (see Figure 3.8 B).
This suggests that only larger domes, regardless of their shape, possess
the capability to produce folds in the middle.

Furthermore, as expected, we found that the triangular domes buckled
into a Y-shaped network of folds that resembled the pattern observed in
digital domes (see Figure 3.8 D). The timelapse of buckling indicated
that the vertices of the triangular domes pushed the buckling along the
medians of the triangle (see Figure 3.8 C).

We observed that the folds exhibited variability in terms of stability,
with some dissipating into the monolayer while others remained intact
and even formed attachments with each other. These folded structures
were stable for several hours and could be imaged for over 12 hours (see
Figure 3.8E-F). Interestingly, when immediately inflated, these folds
would unfurl themselves into a dome again.

Our results suggest that the MOLI system could provide a novel way of
generating folds, with potential applications in tissue engineering. By
controlling a few mechanical parameters such as geometry and pressure,
it is possible to produce folds of predictable patterns.

![Controling the patterns of fold: A-B Simulations show digital models
of ellipsoidal and triangular domes buckled into line and Y-shaped
junctions. C-D Experimental results confirm the simulation findings. E-F
Confocal z-stack images show the folds in the case of a line and
Y-shaped junction. Scale bar is 50\\mu m.
](media/image54.png){width="6.125in" height="6.766996937882765in"}

***Controling the patterns of fold**: A-B Simulations show digital
models of ellipsoidal and triangular domes buckled into line and
Y-shaped junctions. C-D Experimental results confirm the simulation
findings. E-F Confocal z-stack images show the folds in the case of a
line and Y-shaped junction. Scale bar is* $50\mu m$*.*

### Summary and Discussion

We utilized our device to generate dome from a flat monolayer then
transform it into folds, alongside investigating the buckling response
in relation to actin remodeling timescales. We discovered that buckling
occurs at various scales, starting from the tissue level down to the
actin cortex of individual cells, and is triggered when deflation occurs
more rapidly than actin can remodel. We then explored the patterns of
folding that emerge from different sized and shaped domes, and proposed
a new method of creating controlled folds from planar monolayer. With
the aid of computational models, we demonstrated the engineering
potential of the dome system to produce structured folds by manipulating
the geometry and pressure.

As mentioned earlier, mechanical instabilities are ubiquitous in
biological systems, and the phenomenon of buckling has been observed in
MDCK epithelial monolayers through various methods, such as growth in
confinement or direct application of compression (T. P. J. Wyatt et al.
2020; Trushko et al. 2020). Wyatt et al. demonstrated that compressive
stress greater than 35% strain can cause epithelial monolayers to buckle
out of plane, and showed that active contractility can recover the
out-of-plane deformation within tens of seconds.

Our study, on the other hand, is the first to offer visual insights into
the minute details of the buckling process and its implications for
tissue architecture at multiple scales.

From a mechanistic perspective, our result are a consequence of the
hierarchical structure of the epithelial tissue, which comprises various
components that sustain deformations and forces at different levels.
Notably, the actin cytoskeleton plays a critical role in defining the
shape of cells and tissues at multiple scales (Clarke and Martin 2021).
Additionally, a cell monolayer can be considered as an assembly of cells
with their own surface tension and material properties, indicating a
material with different length scales would buckle at different length
scales. Therefore, if there is a local weakness in a cell or subcellular
feature, it is expected to locally buckle. For instance, we only
observed subcellular-level buckling in very thin cells while overall
tissue doesn't buckle.

Furthermore, the short-wavelength folds resulting from subcellular
buckling are intriguing to consider. It is worth noting that actin
buckling is not a new phenomenon in the field, and there are minimal
models of actin filaments with myosin motors on a lipid membrane
demonstrating that myosin-induced contraction leads to actin filament
buckling (Murrell and Gardel 2012; Costa, Hucker, and Yin 2002; Wang and
Qian 2019). In membrane-actin droplets, researchers have reported
multiple modes in the form of buckling and wrinkling, depending on the
thickness (Kusters et al. 2019). Interestingly, they found that thin
shells undergo buckling and thin shells produce wrinkles in the membrane
but not in actin, which could indicate different modes of buckling
within a cell.

In the context of tissue-scale buckling, our results can be understood
in terms of modes of buckling in thin shells. Our computational model
suggests that the cortex behaves like a hyperelastic material at short
timescales, as in our case by the rate at which we are deflating these
tissues. Similar results would be obtained if we repeated the experiment
with elastic shells. The literature on thin shell buckling reveals
similar aspects, such as the folds and patterns that emerge when
different sized shells buckle (ref).

The slenderness, defined as the ratio of dome radius to thickness,
intuitively guides the different modes of buckling. Thin shells with
high slenderness would lead to a higher mode of buckling compared to
thicker shells. However, our experiments go beyond understanding the
system and show that we can program folds by minimally controlling two
parameters: geometry and pressure. For non-spherical domes, anisotropic
stresses are observed along the axes of the elliptical footprint for
ellipsoidal domes (ref). These stresses can orient the folding in a
particular direction to generate a programmed fold, such as Y junctions
on the sides of a rectangular footprint.

In summary, this thesis presents a novel experimental system that allows
us to inflate epithelial domes and deflate them into tubes. We
demonstrate that the timescales of actomyosin cytoskeleton remodeling
play a key role in this transformation. By controlling the geometry of
the epithelia and the rate of deflation, we show that we can engineer
epithelial folds of desired geometry.

## Conclusions and Future Perspectives

### Conclusions

The main conclusions of this study are as follows:

1.  We have developed a microfluidics-based system for generating 3D
    epithelia using micropatterning technique PRIMO to create a
    non-adhesive region from which epithelial monolayers can detach and
    inflate into a dome.

2.  Using the MOLI technique, we probed the mechanics of epithelial
    domes subjected to constant pressure and found that the dome reaches
    a steady state after five minutes of applying pressure. These
    experiments revealed a non-monotonic tension-strain response due to
    geometric constraints.

3.  The constitutive response of the epithelial tissue showed that the
    domes exhibit an initial increase in tension with strain, tending to
    a tensional plateau at high strains, consistent with earlier studies
    demonstrating superelastic behavior in epithelia.

4.  Dynamic material testing of domes with varying inflation/deflation
    rates demonstrated that the active viscoelasticity of the cortical
    network directs epithelial rheology.

5.  We developed a complementary model to understand the different
    timescales involved in the tissue stretching process.

6.  The epithelial tissue behaves like an active viscoelastic fluid,
    exhibiting hyperelastic behavior at short timescales and
    viscoelastic behavior at slower scales.

7.  Rapid deflation to -50 Pa, faster than the remodeling timescales,
    leads to buckling instability.

8.  Buckling occurs at multiple scales, from the subcellular level to
    the tissue level, with differing characteristic lengths of the
    folds. The shortest folds occur at the membrane cortex level, and
    the longest at the tissue scale.

9.  Different sized spherical domes create different patterns. Smaller
    domes buckle into a fold along their periphery, while larger ones
    tend to create a network of folds in the center.

10. Folds can be programmed by controlling the shape of the dome.
    Elliptical domes produce a fold along the major axis, while
    triangular domes produce a Y-shaped network in the middle.

### Future Perspectives

The experiments and theory presented in this thesis focus on the active
viscoelasticity of tissues and the generation of folds using buckling
instability. However, this experimental setup has implications for
several projects within our research group.

For example, the current experiments only examined short timescales
(\<10-30 minutes) and focused solely on the actin cytoskeleton.
Investigating the role of other cytoskeletal components, such as
intermediate filaments, would be of great interest. Past studies have
shown that intermediate filaments are critical in tissue re-stiffening.
My colleague, Tom Golde, is currently using MOLI to study intermediate
filament networks.

In addition, we are also utilizing the MOLI device to study a variety of
different tissues, including stem-cell tissues, cancer tissue, and
organoids. This could enable us to investigate the interplay between
geometry, pressure, and cell fate. The inverted cell culture method we
use also allows for high-resolution imaging. Two-channel system provides
a conducive environment for maintaining complex culture conditions as
well as allow for co-culture possibilities.

For the mechanobiology community, our setup is particularly intriguing
because, when the domes are stretched beyond 100%, the nucleus becomes
compressed, which triggers various mechanotransduction pathways. We
could easily examine the role of the nucleus and different
mechanosensitive proteins when subjected to deformation. Additionally,
we could use pharmacological treatments to alter tissue tension and
understand the specific molecular pathways involved in maintaining
tissue shape.

At the molecular scale, we could also investigate focal adhesions during
delamination. Our experimental system delaminates tissue from the
substrate, which presents an opportunity to study cell-substrate
adhesion using protein patterning and live-cell imaging with focal
adhesion markers. Furthermore, experiments conducted over longer
timescales could allow us to explore the mechanics of cell-cell
junctions and cellular rearrangements in response to prolonged
stretching.

I must note the tissue hydraulic aspect, which has been largely
overlooked in this thesis. Specifically, we have not extensively
explored the trans-epithelial flow due to its negligible effect on our
timescale. However, recent studies have demonstrated that the epithelial
tissue can function as an active mechano-biological pump, generating its
own pressure gradient over longer timescales. Thus, it would be
worthwhile to investigate the role of fluid transport under controlled
pressure in our microfluidic system.

Through my work with this system, I have identified numerous promising
directions for future research. One particularly intriguing project, led
by Thomas Wilson, involves the implementation of concepts such as shape
changing, self-healing, and flexible epithelia in the creation of
biohybrid devices. Our initial approach will involve the construction of
a microfluidic chip, where the channels are composed of epithelial
tissues that can be manipulated using optogenetic tools to open or close
specific segments, akin to valves. This endeavor will enable us to
generate novel synthetic epithelial tissue systems and develop a more
comprehensive understanding of the underlying physical principles
driving morphogenesis.

# Appendices {#appendices-1}

## Methods and Materials

### Fabrication of microfluidic devices

Polydimethylsiloxane (PDMS) gels (Sylgard PDMS kit, Dow Corning) were
used to make the microfluidic devices. PDMS was synthesized by mixing
the curing agent and elastomer in 1:9 weight ratio. This mixture was
centrifuged for 2min at 900rpm to remove air bubbles. The unpolymerized
PDMS was poured into a mold or spun to obtain the desired shape.

There are four parts to the device (figgg). First is the top block, a
thick PDMS block with four inlets and one channel for the application of
hydraulic pressure. The second is a $200\mu m$ thin PDMS layer with a
$1.2mm$ diameter hole in the center with a $400nm$ porous membrane
(Polycarbonate filtration membrane $0.4\mu m$, Whatman membranes)
attached to it. The third is another $200\mu m$ thin PDMS layer with a
channel for seeding the cells. Lastly, all these PDMS parts are attached
to, the fourth part, a glass-bottomed 35mm dish ($35mm,no.1.5\#$
coverslip thickness, Cellvis).

The top block was made using replica molding in a 3D printed mold. This
mold was 3D printed with vat polymerization and a digital light
processing 3D printer (Solus DLP 3D Printer with SolusProto resin). The
mold's surface was then silanized using Trichlorosilane
(Trichloro(1H,1H,2H,2H-perfluorooctyl) silane, Merck) for preventing
adhesion with unpolymerized PDMS. PDMS was poured into the mold and
degassed for one hour. PDMS is cured with a hot plate at \$100\\degree
C\$ for $30min$. Once cured, PDMS is removed, cut into devices, and
punched with $1.5mm$. $200\mu m$ thin PDMS layers were made by spin
coating $4.5ml$ unpolymerized PDMS on a $15cm$ dish at $500rpm$ for
$1min$. These dishes were incubated in an oven at \$80\\degree C\$ to
polymerize for 12hr. These thin sheets were cut into the parts of
devices using a Silhouette cutting machine (Silhouette Cameo 4,
Silhouette America). The sheets were attached to a Silhouette cutting
mat and then Silhouette software was fed with the pattern of the device
layers. A sharp cutting tool in the machine cut the PDMS along the
pattern. These cut PDMS were peeled off with help of $70\%$ ethanol.

These devices are assembled with the aid of ozone plasma cleaner
(PCD-002-CE, Harrick Plasma). Glass bottomed dishes and thin PDMS layers
with cell channels were treated for $1min$ under plasma. Then bonded
together by placing the layers in contact for $2hr$ at \$80 \\degree
C\$. Similarly, the top block and thin membrane with porous membrane
were also bonded. These layers were later bonded together again using
plasma cleaner.

### Patterning protein on the device

The devices were filled with $96\%$ ethanol for removing air bubbles.
Then, devices are treated with $5\%$ v/v (3-aminopropyl) triethoxysilane
(Merck) diluted in $96\%$ ethanol for $3min$ and rinse three times with
$96\%$ ethanol. Later the devices were filled with MilliQ water to
remove ethanol traces. PRIMO (Alveole Lab) was used to pattern
adhesion-promoting protein. For this setup, devices were incubated with
PLL (Poly-L-lysine solution, Merck) for $1hr$, subsequently with SVA PEG
($50mg/ml$ in $8.24pH$ HEPES) for $30min$, and rinsed with HEPES. Before
using PRIMO, devices were filled with a photoinitiator. Desired protein
pattern was loaded into the PRIMO software (Leonardo, Alveole Lab).

PRIMO uses a microscope to shine the laser in the specific region
according to the loaded pattern to cut PEG chains. After the PRIMO
process, the samples were rinsed with phosphate-buffered saline (PBS,
Merck). Then the samples were filled with fibronectin and fibrinogen
($100\mu g/ml$ Fibronectin in $2\%$ Far-red fibrinogen solution in 1X
PBS) solution for $5min$. Then samples were rinsed again with 1X PBS.
Fibrinogen labels the fibronectin with Far-red signal to image the
coated protein pattern and allows for tracking the position of the
domes. The PRIMOed samples can be stored at \$4\\degree C\$ for two to
three days before seeding cells.

### Cell culture in the device

To image cell shape and tissue structure Madin-Darby Canine Kidney
(MDCK) cells expressing CIBN-GFP-CAAX were used for the experiments.
CIBN-GFP-CAAX labels the plasma membrane. These cells were cultured in
Dulbecco's Modified Eagle Medium (DMEM, Gibco Thermofisher) with $10\%$
v/v fetal bovine serum (FBS, Gibco, Thermofisher), L-glutamine
(Thermofisher), $100\mu g/ml$ streptomycin and penicillin. Cells were
incubated at \$37\\degree C\$ with a $5\%$ $CO_{2}$ condition.

Before seeding cells in the device, it is filled with a cell culture
medium. Cells are trypsinized and diluted at a concentration of
$25 - 30 \times 10^{6}cells/ml$. The cell channel of the device is
filled with $30\mu l$ of cell solution and incubated for cell adhesion.
After one hour of incubation, devices are rinsed with media to remove
unattached cells. Devices were kept $24hr$ in the incubation for the
growth of a monolayer before the experiment. It is important to note
that the inverted epifluorescence microscope is need to see the cells.
The bright-field microscope can not be used for visualizing cells
because of the porous membrane.

### Staining actin with SPY-actin

To observe the dynamics of the cortex, we used SPY555-actin
(Spirochrome), a bright dye optimized for quick labeling of F-actin in
live cells with low background. To prepare the 1000x solution, we added
$50\mu l$ of anhydrous DMSO to the stock SPY555-actin. We then added
$1\mu l$ of the 1000x solution to $999\mu l$ of cell culture medium. The
resulting solution was introduced into the microfluidic chips and left
in the incubator for 2 hours before imaging.

### Fabrication method for the Light-Sheet MOLI device 

The devices used with the light-sheet microscope consisted of a single
PDMS block bonded to a glass microscope slide ($76 \times 26mm$, RS
Components BPB016). The blocks were made using a 3D printed mold
(Ultimaker 3 with Ultimaker PLA Printer Filament 1616). PDMS was mixed,
centrifuged, degassed, and cured as described above for the normal
devices. Once cured, the PDMS was removed, cut into individual devices
and punched with a 1.5mm biopsy punch. The PDMS blocks were then
attached glass slides using a thin layer of unpolymerized PDMS, that was
coated onto the glass slides using a spatula. The devices were then kept
on a hotplate at \$100\\degree C\$ for $30min$ to allow the PDMS bonding
to fully cure. The $400nm$ porous membranes were then attached to the
devices. The edges of the membrane were carefully dipped into
unpolymerized PDMS, before being placed flat on the top of the device.
Particular care was taken to ensure the center of the membrane over the
punched pressure-application hole remained free of PDMS. The devices
were then kept at \$65\\degree C\$ for an hour to allow the PDMS bonding
to fully cure.

### Device protein patterning and cell culture in Light-Sheet device

The light-sheet devices were protein patterned and cell cultured using
the same methods and steps as outlined above for the normal devices,
with the one minor addition of the use of a simple PDMS and glass cap
for a few critical steps. The porous membrane for pressure application,
and thus the site of protein patterning and cell seeding, for the
light-sheet devices is exposed and on the top side of the devices. This
mostly allowed for easy application of reagents as a droplet could be
applied and aspirated directly.

However for the more sensitive steps in the procedure, a simple PDMS and
glass device was used to create a temporary covered channel over the
porous membrane to regulate the procedure and ensure the treatment of
the devices was highly standardized. Specifically, the cap was used for
the application of photoinitiator during PRIMO, and for the application
of cell solution during cell attachment. The caps were fabricated using
$2cm \times 2cm$ squares of a $400\mu m$ thick PDMS layer, with a
keyhole shape cut in from the side. Each PDMS piece was then stuck to a
$18mm$ diameter coverslip ($18mm$, $1\#$ Cover glasses circular,
Marienfeld 0111580) using the surface tension of the liquid. The
experimental apparatus and measurements for the light-sheet devices were
the same as the normal devices as outlined above.

### Application and measurement of the pressure

The pressure is applied via hydrostatic forces similar to the previous
studies (Choudhury et al. 2022; Palmer et al. 2021). The two channels in
the chip were separated by the porous membrane. Cells are on the bottom
side of the membrane. The pressure in the channel (top side of the
membrane) is used to inflate the structures on the top. This channel has
one inlet and one outlet for removing bubbles. The inlet is connected to
a $35ml$ reservoir of cell culture medium (in a $50ml$ falcon tube) by
tubing (PTFE Tubing $1/16inch$ OD for Microfluidics, Darwin
microfluidics) and the outlet is connected to a shutoff valve
(Microfluidic Sample Injection / Shut-off Valve, Darwin microfluidics).
Once bubbles are removed, closing the valve would apply the pressure on
the basal side of the cells according to the difference between the
height of the fluid level. All tubings are connected to the chip with a
steel insert (Stainless steel 90deg Bent PDMS Couplers, Darwin
microfluidics). We are able to find zero by matching the height of the
device to the liquid and air interface in the reservoir. This is
confirmed with the experiments, where on applying pressure domes form
but on slow reduction in pressure to zero causes domes to deflate.

### Confocal Microscopy

For timelapse imaging of domes at a larger time interval (\> 1 min), an
inverted Nikon microscope with a spinning disk confocal unit (CSU-W1,
Yokogawa) was used with Nikon 40x, 20x, and 10x air lenses. For shorter
time intervals (\< 10 s), a Zeiss LSM880 inverted confocal microscope
was used with laser scanning mode. Fast imaging was enabled by imaging a
single line in the middle of the dome.

### Light-sheet microscopy

The imaging of the light-sheet devices was done with a dual-illumination
inverted Selective Plane Illumination Microscope (diSPIM) (QuVi SPIM,
Luxendo, Brucker) with Nikon 40x immersion lenses (Nikon CFI Apo 40x W
0.8 NA NIR water immersion objective). For the buckling experiments,
only single objective illumination and detection was used for the fast
imaging of $2s/frame$.

### Quantification of the dome areal strain and tension

As mentioned earlier, the domes were imaged in 3D with confocal
microscopy. We used ImageJ to manually section the dome in the middle in
the YZ plane, XZ plane is a plane parallel to the monolayer, with
Reslice function along the Z axis. This section was used to calculate
the height (h), radius of curvature (R), and base radius (a). Strain
($\epsilon$) and tension ($\sigma$) were calculated as,

$$\epsilon = \frac{h^{2}}{a^{2}},\ \ \ \ and\ \ \ \ \sigma = \frac{\Delta PR}{2}.$$

The raw data was extracted in ImageJ and then MATLAB was used to compute
and plot the strain and tension.

### Analysis of the kymographs

For cyclic pressure or buckling experiments, the domes were imaged at
low resolution and high noise levels to capture fast dynamics. The
previous method of manually quantifying each time point is not feasible.
Thus, we used the ImageJ function of the Reslice function along the time
axis. We resliced it along the Y-time axis in the middle of the dome,
such that we get a kymograph of height as a function of time. Also, we
performed the reslicing along the XT axis at the plane of the monolayer,
such that we get the kymograph of the base radius with respect to time.
These kymographs were in form of images save manually with ImageJ.

A custom-built MATLAB code was used to digitize the kymographs, where
maximum intensity along each time was considered as the current dome
height position. The first $30s$ of the experiment pressure is zero, so
the unstretched monolayer position is determined from those time points.
Dome height is calculated with the difference between the current
position and the initial position. Base radius is calculated similarly
by subtracting two sides. The radius of curvature is calculated using
the relation between the base and height of the dome as

$$R = \left( h^{2} + a^{2} \right)/2h.$$

### Qualitative analysis of the buckling event

Whether domes are buckling or not was determined manually checking every
frame during the deflation. If dome maintains the smooth circular
geometry in XZ plane during the deflation, we mark the dome as "not
buckling". However, if the dome has a visual discontinuity in the
curvature or a kink it is then considered to be "buckling".

Imaging the fast events in XY plane was done in an ad hoc manner. To
capture the folds, the dome as imaged closer to the apical surface of
the monolayer. The type of fold was determined by carefully observing
the way which monolayer makes contact with the imaging plane. If there
is one point of contact in the center and spreads outwards, it is
considered as accumulation along the periphery. In case where there are
multiple points of contact and they all join in the middle, it is
considered as a network of folds.

"A Ton for Thompson's Tome." 2017. *Nature Physics* 13 (4): 315--15.
<https://doi.org/10.1038/nphys4096>.

Adriaen Backer Wikipedia. 1670. "Dutch: Anatomische Les van Dr. Frederik
Ruysch Anatomy Lesson by Prof. Frederik Ruysch.label
QS:Lnl,\"Anatomische Les van Prof. Frederik Ruysch.\"."

Alberts, Bruce. 2015. *Molecular Biology of the Cell*. Sixth edition.
New York, NY: Garland Science, Taylor and Francis Group.

Alt, Silvanus, Poulami Ganguly, and Guillaume Salbreux. 2017. "Vertex
Models: From Cell Mechanics to Tissue Morphogenesis." *Philosophical
Transactions of the Royal Society B: Biological Sciences* 372 (1720):
20150520. <https://doi.org/10.1098/rstb.2015.0520>.

Ambrosi, Davide, Martine Ben Amar, Christian J. Cyron, Antonio DeSimone,
Alain Goriely, Jay D. Humphrey, and Ellen Kuhl. 2019. "Growth and
Remodelling of Living Tissues: Perspectives, Challenges and
Opportunities." *Journal of The Royal Society Interface* 16 (157):
20190233. <https://doi.org/10.1098/rsif.2019.0233>.

"Animal Tissues. Covering Epithelium. Atlas of Plant and Animal
Histology." n.d.
https://mmegias.webs.uvigo.es/02-english/guiada_a\_revestimiento.php.

"Are All Fish the Same Shape If You Stretch Them? The Victorian Tale of
On Growth and Form." n.d.
https://writings.stephenwolfram.com/2017/10/are-all-fish-the-same-shape-if-you-stretch-them-the-victorian-tale-of-on-growth-and-form/.

Arif, Zia Ullah, Muhammad Yasir Khalid, Waqas Ahmed, and Hassan Arshad.
2022. "A Review on Four-Dimensional (4D) Bioprinting in Pursuit of
Advanced Tissue Engineering Applications." *Bioprinting* 27 (August):
e00203. <https://doi.org/10.1016/j.bprint.2022.e00203>.

Balasubramaniam, Lakshmi, Amin Doostmohammadi, Thuan Beng Saw, Gautham
Hari Narayana Sankara Narayana, Romain Mueller, Tien Dang, Minnah
Thomas, et al. 2021. "Investigating the Nature of Active Forces in
Tissues Reveals How Contractile Cells Can Form Extensile Monolayers."
*Nature Materials* 20 (8): 1156--66.
<https://doi.org/10.1038/s41563-021-00919-2>.

Bao, G., and S. Suresh. 2003. "Cell and Molecular Mechanics of
Biological Materials." *Nature Materials* 2 (11): 715--25.
<https://doi.org/10.1038/nmat1001>.

Barker, Nick. 2014. "Adult Intestinal Stem Cells: Critical Drivers of
Epithelial Homeostasis and Regeneration." *Nature Reviews Molecular Cell
Biology* 15 (1): 19--33. <https://doi.org/10.1038/nrm3721>.

Bartolo, Denis, Guillaume Degré, Philippe Nghe, and Vincent Studer.
2008. "Microfluidic Stickers." *Lab on a Chip* 8 (2): 274--79.
<https://doi.org/10.1039/B712368J>.

Blanch-Mercader, C., V. Yashunsky, S. Garcia, G. Duclos, L. Giomi, and
P. Silberzan. 2018. "Turbulent Dynamics of Epithelial Cell Cultures."
*Physical Review Letters* 120 (20): 208101.
<https://doi.org/10.1103/PhysRevLett.120.208101>.

Blonski, Slawomir, Julien Aureille, Sara Badawi, Damian Zaremba, Lydia
Pernet, Alexei Grichine, Sandrine Fraboulet, et al. 2021. "Direction of
Epithelial Folding Defines Impact of Mechanical Forces on Epithelial
State." *Developmental Cell* 56 (23): 3222--3234.e6.
<https://doi.org/10.1016/j.devcel.2021.11.008>.

Bourke, J. R., T. Matainaho, G. J. Huxham, and S. W. Manley. 1987.
"Cyclic AMP-stimulated Fluid Transport in the Thyroid: Influence of
Thyroid Stimulators, Amiloride and Acetazolamide on the Dynamics of
Domes in Monolayer Cultures of Porcine Thyroid Cells." *Journal of
Endocrinology* 115 (1): 19--NP. <https://doi.org/10.1677/joe.0.1150019>.

Braga, Vania. 2016. "Spatial Integration of E-cadherin Adhesion,
Signalling and the Epithelial Cytoskeleton." *Current Opinion in Cell
Biology*, Cell dynamics, 42 (October): 138--45.
<https://doi.org/10.1016/j.ceb.2016.07.006>.

Brassard, Jonathan A., Mike Nikolaev, Tania Hübscher, Moritz Hofer, and
Matthias P. Lutolf. 2021. "Recapitulating Macro-Scale Tissue
Self-Organization Through Organoid Bioprinting." *Nature Materials* 20
(1): 22--29. <https://doi.org/10.1038/s41563-020-00803-5>.

Breau, Keith A., Meryem T. Ok, Ismael Gomez-Martinez, Joseph Burclaff,
Nathan P. Kohn, and Scott T. Magness. 2022. "Efficient Transgenesis and
Homology-Directed Gene Targeting in Monolayers of Primary Human Small
Intestinal and Colonic Epithelial Stem Cells." *Stem Cell Reports* 17
(6): 1493--1506. <https://doi.org/10.1016/j.stemcr.2022.04.005>.

Brown, Theodore M., and Elizabeth Fee. 2006. "Rudolf Carl Virchow."
*American Journal of Public Health* 96 (12): 2104--5.
<https://doi.org/10.2105/AJPH.2005.078436>.

Brugués, Agustí, Ester Anon, Vito Conte, Jim H. Veldhuis, Mukund Gupta,
Julien Colombelli, José J. Muñoz, G. Wayne Brodland, Benoit Ladoux, and
Xavier Trepat. 2014. "Forces Driving Epithelial Wound Healing." *Nature
Physics* 10 (9): 683--90. <https://doi.org/10.1038/nphys3040>.

Bryant, David M., and Keith E. Mostov. 2008. "From Cells to Organs:
Building Polarized Tissue." *Nature Reviews Molecular Cell Biology* 9
(11): 887--901. <https://doi.org/10.1038/nrm2523>.

Calzolari, Simone, Javier Terriente, and Cristina Pujades. 2014. "Cell
Segregation in the Vertebrate Hindbrain Relies on Actomyosin Cables
Located at the Interhombomeric Boundaries." *The EMBO Journal* 33 (7):
686--701. <https://doi.org/10.1002/embj.201386003>.

Cameron, Gladys. 1953. "Secretory Activity of the Chorioid Plexus in
Tissue Culture." *The Anatomical Record* 117 (1): 115--25.
<https://doi.org/10.1002/ar.1091170109>.

Campàs, Otger, Tadanori Mammoto, Sean Hasso, Ralph A. Sperling, Daniel
O'Connell, Ashley G. Bischof, Richard Maas, David A. Weitz, L.
Mahadevan, and Donald E. Ingber. 2014. "Quantifying Cell-Generated
Mechanical Forces Within Living Embryonic Tissues." *Nature Methods* 11
(2): 183--89. <https://doi.org/10.1038/nmeth.2761>.

Carlier, François M., Charlotte de Fays, and Charles Pilette. 2021.
"Epithelial Barrier Dysfunction in Chronic Respiratory Diseases."
*Frontiers in Physiology* 12.

Cartagena-Rivera, Alexander X., Jeremy S. Logue, Clare M. Waterman, and
Richard S. Chadwick. 2016. "Actomyosin Cortical Mechanical Properties in
Nonadherent Cells Determined by Atomic Force Microscopy." *Biophysical
Journal* 110 (11): 2528--39.
<https://doi.org/10.1016/j.bpj.2016.04.034>.

Casares, Laura, Romaric Vincent, Dobryna Zalvidea, Noelia Campillo,
Daniel Navajas, Marino Arroyo, and Xavier Trepat. 2015. "Hydraulic
Fracture During Epithelial Stretching." *Nature Materials* 14 (3):
343--51. <https://doi.org/10.1038/nmat4206>.

Cavanaugh, Kate E, Michael F Staddon, Shiladitya Banerjee, and Margaret
L Gardel. 2020. "Adaptive Viscoelasticity of Epithelial Cell Junctions:
From Models to Methods." *Current Opinion in Genetics & Development* 63
(August): 86--94. <https://doi.org/10.1016/j.gde.2020.05.018>.

Cederquist, Gustav Y., James J. Asciolla, Jason Tchieu, Ryan M. Walsh,
Daniela Cornacchia, Marilyn D. Resh, and Lorenz Studer. 2019.
"Specification of Positional Identity in Forebrain Organoids." *Nature
Biotechnology* 37 (4): 436--44.
<https://doi.org/10.1038/s41587-019-0085-3>.

Cetera, Maureen, Guillermina R. Ramirez-San Juan, Patrick W. Oakes,
Lindsay Lewellyn, Michael J. Fairchild, Guy Tanentzapf, Margaret L.
Gardel, and Sally Horne-Badovinac. 2014. "Epithelial Rotation Promotes
the Global Alignment of Contractile Actin Bundles During Drosophila Egg
Chamber Elongation." *Nature Communications* 5 (1): 5511.
<https://doi.org/10.1038/ncomms6511>.

Chan, Chii J., and Takashi Hiiragi. 2020. "Integration of Luminal
Pressure and Signalling in Tissue Self-Organization." *Development* 147
(5): dev181297. <https://doi.org/10.1242/dev.181297>.

Chan, Chii Jou, Maria Costanzo, Teresa Ruiz-Herrero, Gregor Mönke, Ryan
J. Petrie, Martin Bergert, Alba Diz-Muñoz, L. Mahadevan, and Takashi
Hiiragi. 2019. "Hydraulic Control of Mammalian Embryo Size and Cell
Fate." *Nature* 571 (7763): 112--16.
<https://doi.org/10.1038/s41586-019-1309-x>.

Chan, Hon Fai, Ruike Zhao, German A. Parada, Hu Meng, Kam W. Leong,
Linda G. Griffith, and Xuanhe Zhao. 2018. "Folding Artificial Mucosa
with Cell-Laden Hydrogels Guided by Mechanics Models." *Proceedings of
the National Academy of Sciences* 115 (29): 7503--8.
<https://doi.org/10.1073/pnas.1802361115>.

Choudhury, Mohammad Ikbal, Morgan A. Benson, and Sean X. Sun. 2022.
"Trans-Epithelial Fluid Flow and Mechanics of Epithelial Morphogenesis."
*Seminars in Cell & Developmental Biology*, Special issue: Human
embryogenesis by Naomi Moris and Marta Shahbazi / Special Issue:
Luminogenesis and Hydraulics in Development by Chii Jou Chan, 131
(November): 146--59. <https://doi.org/10.1016/j.semcdb.2022.05.020>.

Choudhury, Mohammad Ikbal, Yizeng Li, Panagiotis Mistriotis, Ana Carina
N. Vasconcelos, Eryn E. Dixon, Jing Yang, Morgan Benson, et al. 2022.
"Kidney Epithelial Cells Are Active Mechano-Biological Fluid Pumps."
*Nature Communications* 13 (1): 2317.
<https://doi.org/10.1038/s41467-022-29988-w>.

Clarke, D. Nathaniel, and Adam C. Martin. 2021. "Actin-Based Force
Generation and Cell Adhesion in Tissue Morphogenesis." *Current Biology*
31 (10): R667--80. <https://doi.org/10.1016/j.cub.2021.03.031>.

Clément, Raphaël, Benoît Dehapiot, Claudio Collinet, Thomas Lecuit, and
Pierre-François Lenne. 2017. "Viscoelastic Dissipation Stabilizes Cell
Shape Changes During Tissue Morphogenesis." *Current Biology* 27 (20):
3132--3142.e4. <https://doi.org/10.1016/j.cub.2017.09.005>.

Collinet, Claudio, and Thomas Lecuit. 2021. "Programmed and
Self-Organized Flow of Information During Morphogenesis." *Nature
Reviews Molecular Cell Biology* 22 (4): 245--65.
<https://doi.org/10.1038/s41580-020-00318-6>.

Collinet, Claudio, Matteo Rauzi, Pierre-François Lenne, and Thomas
Lecuit. 2015. "Local and Tissue-Scale Forces Drive Oriented Junction
Growth During Tissue Extension." *Nature Cell Biology* 17 (10):
1247--58. <https://doi.org/10.1038/ncb3226>.

Cont, Alice, Tamara Rossy, Zainebe Al-Mayyah, and Alexandre Persat.
2020. "Biofilms Deform Soft Surfaces and Disrupt Epithelia." Edited by
Petra Anne Levin, Gisela Storz, and Howard A Stone. *eLife* 9 (October):
e56533. <https://doi.org/10.7554/eLife.56533>.

Costa, Kevin D., William J. Hucker, and Frank C.-P. Yin. 2002. "Buckling
of Actin Stress Fibers: A New Wrinkle in the Cytoskeletal Tapestry."
*Cell Motility* 52 (4): 266--74. <https://doi.org/10.1002/cm.10056>.

Deforet, M., V. Hakim, H. G. Yevick, G. Duclos, and P. Silberzan. 2014.
"Emergence of Collective Modes and Tri-Dimensional Structures from
Epithelial Confinement." *Nature Communications* 5 (1): 3747.
<https://doi.org/10.1038/ncomms4747>.

Demers, Christopher J., Prabakaran Soundararajan, Phaneendra
Chennampally, Gregory A. Cox, James Briscoe, Scott D. Collins, and
Rosemary L. Smith. 2016. "Development-on-Chip: In Vitro Neural Tube
Patterning with a Microfluidic Device." *Development* 143 (11):
1884--92. <https://doi.org/10.1242/dev.126847>.

Deng, Linhong, Xavier Trepat, James P. Butler, Emil Millet, Kathleen G.
Morgan, David A. Weitz, and Jeffrey J. Fredberg. 2006. "Fast and Slow
Dynamics of the Cytoskeleton." *Nature Materials* 5 (8): 636--40.
<https://doi.org/10.1038/nmat1685>.

Dervaux, Julien, and Martine Ben Amar. 2012. "Mechanical Instabilities
of Gels." *Annual Review of Condensed Matter Physics* 3 (1): 311--32.
<https://doi.org/10.1146/annurev-conmatphys-062910-140436>.

Dessalles, Claire A., Clara Ramón-Lozano, Avin Babataheri, and Abdul I.
Barakat. 2021. "Luminal Flow Actuation Generates Coupled Shear and
Strain in a Microvessel-on-Chip." *Biofabrication* 14 (1): 015003.
<https://doi.org/10.1088/1758-5090/ac2baa>.

Dolega, M. E., M. Delarue, F. Ingremeau, J. Prost, A. Delon, and G.
Cappello. 2017. "Cell-Like Pressure Sensors Reveal Increase of
Mechanical Stress Towards the Core of Multicellular Spheroids Under
Compression." *Nature Communications* 8 (1): 14056.
<https://doi.org/10.1038/ncomms14056>.

Ducuing, Antoine, and Stéphane Vincent. 2016. "The Actin Cable Is
Dispensable in Directing Dorsal Closure Dynamics but Neutralizes
Mechanical Stress to Prevent Scarring in the Drosophila Embryo." *Nature
Cell Biology* 18 (11): 1149--60. <https://doi.org/10.1038/ncb3421>.

Dudin, Omaya, Andrej Ondracka, Xavier Grau-Bové, Arthur AB Haraldsen,
Atsushi Toyoda, Hiroshi Suga, Jon Bråte, and Iñaki Ruiz-Trillo. 2019. "A
Unicellular Relative of Animals Generates a Layer of Polarized Cells by
Actomyosin-Dependent Cellularization." Edited by Mukund Thattai, K
VijayRaghavan, and Mukund Thattai. *eLife* 8 (October): e49801.
<https://doi.org/10.7554/eLife.49801>.

Dulbecco, Renato, and Sharon Okada. 1980. "Differentiation and
Morphogenesis of Mammary Cells in Vitro." *Proceedings of the Royal
Society of London. Series B. Biological Sciences* 208 (1173): 399--408.
<https://doi.org/10.1098/rspb.1980.0058>.

Dumortier, Julien G., Mathieu Le Verge-Serandour, Anna Francesca
Tortorelli, Annette Mielke, Ludmilla de Plater, Hervé Turlier, and
Jean-Léon Maître. 2019. "Hydraulic Fracturing and Active Coarsening
Position the Lumen of the Mouse Blastocyst." *Science*, August.
<https://doi.org/10.1126/science.aaw7709>.

Duque, Julia, Alessandra Bonfanti, Jonathan Fouchard, Emma Ferber,
Andrew Harris, Alexandre J. Kabla, and Guillaume T. Charras. 2023.
"Fracture in Living Cell Monolayers." bioRxiv.
<https://doi.org/10.1101/2023.01.05.522736>.

Eisenhoffer, George T., and Jody Rosenblatt. 2013. "Bringing Balance by
Force: Live Cell Extrusion Controls Epithelial Cell Numbers." *Trends in
Cell Biology* 23 (4): 185--92.
<https://doi.org/10.1016/j.tcb.2012.11.006>.

Elosegui-Artola, Alberto, Ion Andreu, Amy E. M. Beedle, Ainhoa Lezamiz,
Marina Uroz, Anita J. Kosmalska, Roger Oria, et al. 2017. "Force
Triggers YAP Nuclear Entry by Regulating Transport Across Nuclear
Pores." *Cell* 171 (6): 1397--1410.e14.
<https://doi.org/10.1016/j.cell.2017.10.008>.

Elosegui-Artola, Alberto, Anupam Gupta, Alexander J. Najibi, Bo Ri Seo,
Ryan Garry, Christina M. Tringides, Irene de Lázaro, et al. 2022.
"Matrix Viscoelasticity Controls Spatiotemporal Tissue Organization."
*Nature Materials*, December, 1--11.
<https://doi.org/10.1038/s41563-022-01400-4>.

Elosegui-Artola, Alberto, Roger Oria, Yunfeng Chen, Anita Kosmalska,
Carlos Pérez-González, Natalia Castro, Cheng Zhu, Xavier Trepat, and
Pere Roca-Cusachs. 2016. "Mechanical Regulation of a Molecular Clutch
Defines Force Transmission and Transduction in Response to Matrix
Rigidity." *Nature Cell Biology* 18 (5): 540--48.
<https://doi.org/10.1038/ncb3336>.

Engler, Adam J., Shamik Sen, H. Lee Sweeney, and Dennis E. Discher.
2006. "Matrix Elasticity Directs Stem Cell Lineage Specification."
*Cell* 126 (4): 677--89. <https://doi.org/10.1016/j.cell.2006.06.044>.

Fasano, A, B Baudry, D W Pumplin, S S Wasserman, B D Tall, J M Ketley,
and J B Kaper. 1991. "Vibrio Cholerae Produces a Second Enterotoxin,
Which Affects Intestinal Tight Junctions." *Proceedings of the National
Academy of Sciences* 88 (12): 5242--46.
<https://doi.org/10.1073/pnas.88.12.5242>.

Fernández, Pablo A., Benedikt Buchmann, Andriy Goychuk, Lisa K.
Engelbrecht, Marion K. Raich, Christina H. Scheel, Erwin Frey, and
Andreas R. Bausch. 2021. "Surface-Tension-Induced Budding Drives
Alveologenesis in Human Mammary Gland Organoids." *Nature Physics* 17
(10): 1130--36. <https://doi.org/10.1038/s41567-021-01336-7>.

Fierling, Julien, Alphy John, Barthélémy Delorme, Alexandre Torzynski,
Guy B. Blanchard, Claire M. Lye, Anna Popkova, et al. 2022.
"Embryo-Scale Epithelial Buckling Forms a Propagating Furrow That
Initiates Gastrulation." *Nature Communications* 13 (1): 3348.
<https://doi.org/10.1038/s41467-022-30493-3>.

Firmin, Julie, Nicolas Ecker, Diane Rivet Danon, Virginie Barraud Lange,
Hervé Turlier, Catherine Patrat, and Jean-Léon Maître. 2022. "Mechanics
of Human Embryo Compaction." bioRxiv.
<https://doi.org/10.1101/2022.01.09.475429>.

Fletcher, Daniel A., and R. Dyche Mullins. 2010. "Cell Mechanics and the
Cytoskeleton." *Nature* 463 (7280): 485--92.
<https://doi.org/10.1038/nature08908>.

Fortunato, Isabela C., and Raimon Sunyer. 2022. "The Forces Behind
Directed Cell Migration." *Biophysica* 2 (4): 548--63.
<https://doi.org/10.3390/biophysica2040046>.

Fouchard, Jonathan, Tom P. J. Wyatt, Amsha Proag, Ana Lisica, Nargess
Khalilgharibi, Pierre Recho, Magali Suzanne, Alexandre Kabla, and
Guillaume Charras. 2020. "Curling of Epithelial Monolayers Reveals
Coupling Between Active Bending and Tissue Tension." *Proceedings of the
National Academy of Sciences* 117 (17): 9377--83.
<https://doi.org/10.1073/pnas.1917838117>.

Gallaire, François, and P.-T. Brun. 2017. "Fluid Dynamic Instabilities:
Theory and Application to Pattern Forming in Complex Media."
*Philosophical Transactions of the Royal Society A: Mathematical,
Physical and Engineering Sciences* 375 (2093): 20160155.
<https://doi.org/10.1098/rsta.2016.0155>.

Gjorevski, Nikolce, Norman Sachs, Andrea Manfrin, Sonja Giger, Maiia E.
Bragina, Paloma Ordóñez-Morán, Hans Clevers, and Matthias P. Lutolf.
2016. "Designer Matrices for Intestinal Stem Cell and Organoid Culture."
*Nature* 539 (7630): 560--64. <https://doi.org/10.1038/nature20168>.

Gjorevski, N., M. Nikolaev, T. E. Brown, O. Mitrofanova, N. Brandenberg,
F. W. DelRio, F. M. Yavitt, P. Liberali, K. S. Anseth, and M. P. Lutolf.
2022. "Tissue Geometry Drives Deterministic Organoid Patterning."
*Science*, January. <https://doi.org/10.1126/science.aaw9021>.

Godard, Benoit G, and Carl-Philipp Heisenberg. 2019. "Cell Division and
Tissue Mechanics." *Current Opinion in Cell Biology*, Cell Dynamics, 60
(October): 114--20. <https://doi.org/10.1016/j.ceb.2019.05.007>.

Gómez-Gálvez, Pedro, Pablo Vicente-Munuera, Samira Anbari, Javier
Buceta, and Luis M. Escudero. 2021. "The Complex Three-Dimensional
Organization of Epithelial Tissues." *Development* 148 (1): dev195669.
<https://doi.org/10.1242/dev.195669>.

Gómez-González, Manuel, Ernest Latorre, Marino Arroyo, and Xavier
Trepat. 2020. "Measuring Mechanical Stress in Living Tissues." *Nature
Reviews Physics* 2 (6): 300--317.
<https://doi.org/10.1038/s42254-020-0184-6>.

Good, Matthew, and Xavier Trepat. 2018. "Cell Parts to Complex
Processes, from the Bottom Up." *Nature* 563 (7730): 188--89.
<https://doi.org/10.1038/d41586-018-07246-8>.

Gorfinkiel, Nicole, and Alfonso Martinez Arias. 2021. "The Cell in the
Age of the Genomic Revolution: Cell Regulatory Networks." *Cells &
Development*, Quantitative Cell and Developmental Biology, 168
(December): 203720. <https://doi.org/10.1016/j.cdev.2021.203720>.

Graner, François, and Daniel Riveline. 2017. "'The Forms of Tissues, or
Cell-aggregates': D'Arcy Thompson's Influence and Its Limits."
*Development* 144 (23): 4226--37. <https://doi.org/10.1242/dev.151233>.

Guillamat, Pau, Carles Blanch-Mercader, Guillaume Pernollet, Karsten
Kruse, and Aurélien Roux. 2022. "Integer Topological Defects Organize
Stresses Driving Tissue Morphogenesis." *Nature Materials* 21 (5):
588--97. <https://doi.org/10.1038/s41563-022-01194-5>.

Guillot, Charlène, and Thomas Lecuit. 2013. "Mechanics of Epithelial
Tissue Homeostasis and Morphogenesis." *Science* 340 (6137): 1185--89.
<https://doi.org/10.1126/science.1235249>.

Guimarães, Carlos F., Luca Gasperini, Alexandra P. Marques, and Rui L.
Reis. 2020. "The Stiffness of Living Tissues and Its Implications for
Tissue Engineering." *Nature Reviews Materials* 5 (5): 351--70.
<https://doi.org/10.1038/s41578-019-0169-1>.

Guo, Hanqing, Michael Swan, and Bing He. 2022. "Optogenetic Inhibition
of Actomyosin Reveals Mechanical Bistability of the Mesoderm Epithelium
During Drosophila Mesoderm Invagination." Edited by Michel Bagnat, Utpal
Banerjee, Sebastian J Streichan, and Magali Suzanne. *eLife* 11
(February): e69082. <https://doi.org/10.7554/eLife.69082>.

Gutzman, Jennifer H., Ellie Graeden, Isabel Brachmann, Sayumi Yamazoe,
James K. Chen, and Hazel Sive. 2018. "Basal Constriction During
Midbrainhindbrain Boundary Morphogenesis Is Mediated by Wnt5b and Focal
Adhesion Kinase." *Biology Open* 7 (11): bio034520.
<https://doi.org/10.1242/bio.034520>.

Guyon, Joris, Pierre-Olivier Strale, Irati Romero-Garmendia, Andreas
Bikfalvi, Vincent Studer, and Thomas Daubon. 2021. "Co-Culture of
Glioblastoma Stem-like Cells on Patterned Neurons to Study Migration and
Cellular Interactions." *Journal of Visualized Experiments*, no. 168
(February): 62213. <https://doi.org/10.3791/62213>.

Haigo, Saori L., and David Bilder. 2011. "Global Tissue Revolutions in a
Morphogenetic Movement Controlling Elongation." *Science* 331 (6020):
1071--74. <https://doi.org/10.1126/science.1199424>.

Halley, Catherine. 2019. "Public Dissection Was a Gruesome Spectacle."
*JSTOR Daily*.
https://daily.jstor.org/public-dissection-gruesome-spectacle/.

Hannezo, Edouard, and Carl-Philipp Heisenberg. 2022. "Rigidity
Transitions in Development and Disease." *Trends in Cell Biology* 32
(5): 433--44. <https://doi.org/10.1016/j.tcb.2021.12.006>.

Harris, Albert K., Patricia Wild, and David Stopak. 1980. "Silicone
Rubber Substrata: A New Wrinkle in the Study of Cell Locomotion."
*Science* 208 (4440): 177--79.
<https://doi.org/10.1126/science.6987736>.

Harris, Andrew R., Loic Peter, Julien Bellis, Buzz Baum, Alexandre J.
Kabla, and Guillaume T. Charras. 2012. "Characterizing the Mechanics of
Cultured Cell Monolayers." *Proceedings of the National Academy of
Sciences* 109 (41): 16449--54.
<https://doi.org/10.1073/pnas.1213301109>.

Hatzfeld, Mechthild, René Keil, and Thomas M. Magin. 2017. "Desmosomes
and Intermediate Filaments: Their Consequences for Tissue Mechanics."
*Cold Spring Harbor Perspectives in Biology* 9 (6): a029157.
<https://doi.org/10.1101/cshperspect.a029157>.

He, Qian, Takaharu Okajima, Hiroaki Onoe, Agus Subagyo, Kazuhisa Sueoka,
and Kaori Kuribayashi-Shigetomi. 2018. "Origami-Based Self-Folding of
Co-Cultured NIH/3T3 and HepG2 Cells into 3D Microstructures."
*Scientific Reports* 8 (1): 4556.
<https://doi.org/10.1038/s41598-018-22598-x>.

Heer, Natalie C., and Adam C. Martin. 2017. "Tension, Contraction and
Tissue Morphogenesis." *Development* 144 (23): 4249--60.
<https://doi.org/10.1242/dev.151282>.

Helm, Patrick, Mirza Faisal Beg, Michael I. Miller, and Raimond L.
Winslow. 2005. "Measuring and Mapping Cardiac Fiber and Laminar
Architecture Using Diffusion Tensor MR Imaging." *Annals of the New York
Academy of Sciences* 1047 (1): 296--307.
<https://doi.org/10.1196/annals.1341.026>.

Hofer, Moritz, and Matthias P. Lutolf. 2021. "Engineering Organoids."
*Nature Reviews Materials* 6 (5): 402--20.
<https://doi.org/10.1038/s41578-021-00279-y>.

Holzapfel, Gerhard A. 2000. *Nonlinear Solid Mechanics: A Continuum
Approach for Engineering*. Wiley.

Holzapfel, Gerhard A., Ray W. Ogden, and Selda Sherifova. 2019. "On
Fibre Dispersion Modelling of Soft Biological Tissues: A Review."
*Proceedings of the Royal Society A: Mathematical, Physical and
Engineering Sciences* 475 (2224): 20180736.
<https://doi.org/10.1098/rspa.2018.0736>.

Houssin, Nathalie S., Jessica B. Martin, Vincenzo Coppola, Sung Ok Yoon,
and Timothy F. Plageman. 2020. "Formation and Contraction of
Multicellular Actomyosin Cables Facilitate Lens Placode Invagination."
*Developmental Biology* 462 (1): 36--49.
<https://doi.org/10.1016/j.ydbio.2020.02.014>.

Hughes, Alex J., Hikaru Miyazaki, Maxwell C. Coyle, Jesse Zhang, Matthew
T. Laurie, Daniel Chu, Zuzana Vavrušová, Richard A. Schneider, Ophir D.
Klein, and Zev J. Gartner. 2018. "Engineered Tissue Folding by
Mechanical Compaction of the Mesenchyme." *Developmental Cell* 44 (2):
165--178.e6. <https://doi.org/10.1016/j.devcel.2017.12.004>.

Huh, Dongeun, Benjamin D. Matthews, Akiko Mammoto, Martín
Montoya-Zavala, Hong Yuan Hsin, and Donald E. Ingber. 2010.
"Reconstituting Organ-Level Lung Functions on a Chip." *Science* 328
(5986): 1662--68. <https://doi.org/10.1126/science.1188302>.

Humphrey, Jay D. 2002. *Cardiovascular Solid Mechanics*. New York, NY:
Springer New York. <https://doi.org/10.1007/978-0-387-21576-1>.

Humphrey, Jay D., Eric R. Dufresne, and Martin A. Schwartz. 2014.
"Mechanotransduction and Extracellular Matrix Homeostasis." *Nature
Reviews Molecular Cell Biology* 15 (12): 802--12.
<https://doi.org/10.1038/nrm3896>.

Ingber, Donald E. 2018. "From Mechanobiology to Developmentally Inspired
Engineering." *Philosophical Transactions of the Royal Society B:
Biological Sciences* 373 (1759): 20170323.
<https://doi.org/10.1098/rstb.2017.0323>.

Ishida-Ishihara, Sumire, Masakazu Akiyama, Kazuya Furusawa, Isao Naguro,
Hiroki Ryuno, Takamichi Sushida, Seiichiro Ishihara, and Hisashi Haga.
2020. "Osmotic Gradient Induces Stable Dome Morphogenesis on
Extracellular Matrix." *Journal of Cell Science*, January, jcs.243865.
<https://doi.org/10.1242/jcs.243865>.

Ishiguro, Tatsuya, Hirokazu Ohata, Ai Sato, Kaoru Yamawaki, Takayuki
Enomoto, and Koji Okamoto. 2017. "Tumor-Derived Spheroids: Relevance to
Cancer Stem Cells and Clinical Applications." *Cancer Science* 108 (3):
283--89. <https://doi.org/10.1111/cas.13155>.

Ishihara, Keisuke, and Elly M. Tanaka. 2018. "Spontaneous Symmetry
Breaking and Pattern Formation of Organoids." *Current Opinion in
Systems Biology*, Big data acquisition and analysis Development and
differentiation, 11 (October): 123--28.
<https://doi.org/10.1016/j.coisb.2018.06.002>.

Izquierdo, Emiliano, Theresa Quinkler, and Stefano De Renzis. 2018.
"Guided Morphogenesis Through Optogenetic Activation of Rho Signalling
During Early Drosophila Embryogenesis." *Nature Communications* 9 (1):
2366. <https://doi.org/10.1038/s41467-018-04754-z>.

Jalal, Salma, Shidong Shi, Vidhyalakshmi Acharya, Ruby Yun-Ju Huang,
Virgile Viasnoff, Alexander D. Bershadsky, and Yee Han Tee. 2019. "Actin
Cytoskeleton Self-Organization in Single Epithelial Cells and
Fibroblasts Under Isotropic Confinement." *Journal of Cell Science* 132
(5): jcs220780. <https://doi.org/10.1242/jcs.220780>.

Jülicher, Frank, Stephan W. Grill, and Guillaume Salbreux. 2018.
"Hydrodynamic Theory of Active Matter." *Reports on Progress in Physics*
81 (7): 076601. <https://doi.org/10.1088/1361-6633/aab6bb>.

Karzbrun, Eyal, Aimal H. Khankhel, Heitor C. Megale, Stella M. K.
Glasauer, Yofiel Wyle, George Britton, Aryeh Warmflash, et al. 2021.
"Human Neural Tube Morphogenesis in Vitro by Geometric Constraints."
*Nature* 599 (7884): 268--72.
<https://doi.org/10.1038/s41586-021-04026-9>.

Karzbrun, Eyal, Aditya Kshirsagar, Sidney R. Cohen, Jacob H. Hanna, and
Orly Reiner. 2018. "Human Brain Organoids on a Chip Reveal the Physics
of Folding." *Nature Physics* 14 (5): 515--22.
<https://doi.org/10.1038/s41567-018-0046-7>.

Kechagia, Jenny Z., Johanna Ivaska, and Pere Roca-Cusachs. 2019.
"Integrins as Biomechanical Sensors of the Microenvironment." *Nature
Reviews Molecular Cell Biology* 20 (8): 457--73.
<https://doi.org/10.1038/s41580-019-0134-2>.

Kelkar, Manasi, Pierre Bohec, and Guillaume Charras. 2020. "Mechanics of
the Cellular Actin Cortex: From Signalling to Shape Change." *Current
Opinion in Cell Biology* 66 (October): 69--78.
<https://doi.org/10.1016/j.ceb.2020.05.008>.

Khalilgharibi, Nargess, Jonathan Fouchard, Nina Asadipour, Ricardo
Barrientos, Maria Duda, Alessandra Bonfanti, Amina Yonis, et al. 2019.
"Stress Relaxation in Epithelial Monolayers Is Controlled by the
Actomyosin Cortex." *Nature Physics* 15 (8): 839--47.
<https://doi.org/10.1038/s41567-019-0516-6>.

Khoromskaia, Diana, and Guillaume Salbreux. 2023. "Active Morphogenesis
of Patterned Epithelial Shells." Edited by Michael M Kozlov, Naama
Barkai, Benoit Ladoux, Madan Rao, and Jean-Francois Joanny. *eLife* 12
(January): e75878. <https://doi.org/10.7554/eLife.75878>.

Kim, Esther Jeong Yoon, Ekaterina Korotkevich, and Takashi Hiiragi.
2018. "Coordination of Cell Polarity, Mechanics and Fate in Tissue
Self-organization." *Trends in Cell Biology* 28 (7): 541--50.
<https://doi.org/10.1016/j.tcb.2018.02.008>.

Klebe, Robert J., Anne Grant, George Grant, and Paramita Ghosh. 1995.
"Cyclic-AMP Deficient MDCK Cells Form Tubules." *Journal of Cellular
Biochemistry* 59 (4): 453--62. <https://doi.org/10.1002/jcb.240590406>.

Kollmannsberger, Philip, and Ben Fabry. 2011. "Linear and Nonlinear
Rheology of Living Cells." *Annual Review of Materials Research* 41 (1):
75--97. <https://doi.org/10.1146/annurev-matsci-062910-100351>.

Kourouklis, Andreas P., and Celeste M. Nelson. 2018. "Modeling Branching
Morphogenesis Using Materials with Programmable Mechanical
Instabilities." *Current Opinion in Biomedical Engineering*, Tissue
Engineering and Regenerative Medicine / Biomaterials, 6 (June): 66--73.
<https://doi.org/10.1016/j.cobme.2018.03.007>.

Kumar, Aditya, Jesse K. Placone, and Adam J. Engler. 2017.
"Understanding the Extracellular Forces That Determine Cell Fate and
Maintenance." *Development* 144 (23): 4261--70.
<https://doi.org/10.1242/dev.158469>.

Kusters, Remy, Camille Simon, Rogério Lopes Dos Santos, Valentina
Caorsi, Sangsong Wu, Jean-Francois Joanny, Pierre Sens, and Cecile
Sykes. 2019. "Actin Shells Control Buckling and Wrinkling of
Biomembranes." *Soft Matter* 15 (47): 9647--53.
<https://doi.org/10.1039/C9SM01902B>.

Labernadie, Anna, and Xavier Trepat. 2018. "Sticking, Steering,
Squeezing and Shearing: Cell Movements Driven by Heterotypic Mechanical
Forces." *Current Opinion in Cell Biology* 54 (October): 57--65.
<https://doi.org/10.1016/j.ceb.2018.04.008>.

Ladoux, Benoit, and René-Marc Mège. 2017. "Mechanobiology of Collective
Cell Behaviours." *Nature Reviews Molecular Cell Biology* 18 (12):
743--57. <https://doi.org/10.1038/nrm.2017.98>.

Latorre, Ernest, Sohan Kale, Laura Casares, Manuel Gómez-González,
Marina Uroz, Léo Valon, Roshna V. Nair, et al. 2018. "Active
Superelasticity in Three-Dimensional Epithelia of Controlled Shape."
*Nature* 563 (7730): 203--8.
<https://doi.org/10.1038/s41586-018-0671-4>.

Lecuit, Thomas, Pierre-François Lenne, and Edwin Munro. 2011. "Force
Generation, Transmission, and Integration During Cell and Tissue
Morphogenesis." *Annual Review of Cell and Developmental Biology* 27
(1): 157--84. <https://doi.org/10.1146/annurev-cellbio-100109-104027>.

Leggett, Susan E., Alex M. Hruska, Ming Guo, and Ian Y. Wong. 2021. "The
Epithelial-Mesenchymal Transition and the Cytoskeleton in Bioengineered
Systems." *Cell Communication and Signaling* 19 (1): 32.
<https://doi.org/10.1186/s12964-021-00713-2>.

Leighton, Joseph. 1981. "BRIEF HISTORY OF ACTIVE TRANSPORT IN CULTURE."
*Annals of the New York Academy of Sciences* 372 (1 Hormonal Regu):
352--53. <https://doi.org/10.1111/j.1749-6632.1981.tb15487.x>.

Leighton, Joseph, Zbynek Brada, Larry W. Estes, and Gerald Justh. 1969.
"Secretory Activity and Oncogenicity of a Cell Line (MDCK) Derived from
Canine Kidney." *Science* 163 (3866): 472--73.
<https://doi.org/10.1126/science.163.3866.472>.

Lenne, Pierre-François, and Vikas Trivedi. 2022. "Sculpting Tissues by
Phase Transitions." *Nature Communications* 13 (1): 664.
<https://doi.org/10.1038/s41467-022-28151-9>.

Lever, Julia E. 1979. "Regulation of Dome Formation in Differentiated
Epithelial Cell Cultures." *Journal of Supramolecular Structure* 12 (2):
259--72. <https://doi.org/10.1002/jss.400120210>.

Liang, Haiyi, and L. Mahadevan. 2009. "The Shape of a Long Leaf."
*Proceedings of the National Academy of Sciences* 106 (52): 22049--54.
<https://doi.org/10.1073/pnas.0911954106>.

Lomakin, A. J., C. J. Cattin, D. Cuvelier, Z. Alraies, M. Molina, G. P.
F. Nader, N. Srivastava, et al. 2020. "The Nucleus Acts as a Ruler
Tailoring Cell Responses to Spatial Constraints." *Science* 370 (6514):
eaba2894. <https://doi.org/10.1126/science.aba2894>.

Luciano, Marine, Shi-Lei Xue, Winnok H. De Vos, Lorena Redondo-Morata,
Mathieu Surin, Frank Lafont, Edouard Hannezo, and Sylvain Gabriele.
2021. "Cell Monolayers Sense Curvature by Exploiting Active Mechanics
and Nuclear Mechanoadaptation." *Nature Physics* 17 (12): 1382--90.
<https://doi.org/10.1038/s41567-021-01374-1>.

MacCord, Kate. 2012. "Epithelium," November.

Mailand, Erik, Ece Özelçi, Jaemin Kim, Matthias Rüegg, Odysseas
Chaliotis, Jon Märki, Nikolaos Bouklas, and Mahmut Selman Sakar. 2022.
"Tissue Engineering with Mechanically Induced Solid-Fluid Transitions."
*Advanced Materials* 34 (2): 2106149.
<https://doi.org/10.1002/adma.202106149>.

Malandrino, Andrea, Michael Mak, Roger D. Kamm, and Emad Moeendarbary.
2018. "Complex Mechanics of the Heterogeneous Extracellular Matrix in
Cancer." *Extreme Mechanics Letters* 21 (May): 25--34.
<https://doi.org/10.1016/j.eml.2018.02.003>.

Marchiando, Amanda M., W. Vallen Graham, and Jerrold R. Turner. 2010.
"Epithelial Barriers in Homeostasis and Disease." *Annual Review of
Pathology: Mechanisms of Disease* 5 (1): 119--44.
<https://doi.org/10.1146/annurev.pathol.4.110807.092135>.

Marín-Llauradó, Ariadna, Sohan Kale, Adam Ouzeri, Raimon Sunyer,
Alejandro Torres-Sánchez, Ernest Latorre, Manuel Gómez-González, Pere
Roca-Cusachs, Marino Arroyo, and Xavier Trepat. 2022. "Mapping
Mechanical Stress in Curved Epithelia of Designed Size and Shape."
bioRxiv. <https://doi.org/10.1101/2022.05.03.490382>.

Maroudas-Sacks, Yonit, Liora Garion, Lital Shani-Zerbib, Anton Livshits,
Erez Braun, and Kinneret Keren. 2021. "Topological Defects in the
Nematic Order of Actin Fibres as Organization Centres of Hydra
Morphogenesis." *Nature Physics* 17 (2): 251--59.
<https://doi.org/10.1038/s41567-020-01083-1>.

Martin, Adam C., Matthias Kaschube, and Eric F. Wieschaus. 2009. "Pulsed
Contractions of an Actinmyosin Network Drive Apical Constriction."
*Nature* 457 (7228): 495--99. <https://doi.org/10.1038/nature07522>.

Martínez-Ara, Guillermo, Núria Taberner, Mami Takayama, Elissavet
Sandaltzopoulou, Casandra E. Villava, Miquel Bosch-Padrós, Nozomu
Takata, Xavier Trepat, Mototsugu Eiraku, and Miki Ebisuya. 2022.
"Optogenetic Control of Apical Constriction Induces Synthetic
Morphogenesis in Mammalian Tissues." *Nature Communications* 13 (1):
5400. <https://doi.org/10.1038/s41467-022-33115-0>.

Mason, Frank M, and Adam C Martin. 2011. "Tuning Cell Shape Change with
Contractile Ratchets." *Current Opinion in Genetics & Development*,
Developmental mechanisms, patterning and evolution, 21 (5): 671--79.
<https://doi.org/10.1016/j.gde.2011.08.002>.

Matejčić, Marija, and Xavier Trepat. 2020. "Buckling Up from the
Bottom." *Developmental Cell* 54 (5): 569--71.
<https://doi.org/10.1016/j.devcel.2020.08.010>.

---------. 2022. "Mechanobiological Approaches to Synthetic
Morphogenesis: Learning by Building." *Trends in Cell Biology*, July.
<https://doi.org/10.1016/j.tcb.2022.06.013>.

Mertz, Aaron F., Yonglu Che, Shiladitya Banerjee, Jill M. Goldstein,
Kathryn A. Rosowski, Stephen F. Revilla, Carien M. Niessen, M. Cristina
Marchetti, Eric R. Dufresne, and Valerie Horsley. 2013. "Cadherin-Based
Intercellular Adhesions Organize Epithelial Cellmatrix Traction Forces."
*Proceedings of the National Academy of Sciences* 110 (3): 842--47.
<https://doi.org/10.1073/pnas.1217279110>.

Messal, Hendrik A., Silvanus Alt, Rute M. M. Ferreira, Christopher
Gribben, Victoria Min-Yi Wang, Corina G. Cotoi, Guillaume Salbreux, and
Axel Behrens. 2019. "Tissue Curvature and Apicobasal Mechanical Tension
Imbalance Instruct Cancer Morphogenesis." *Nature* 566 (7742): 126--30.
<https://doi.org/10.1038/s41586-019-0891-2>.

Moeendarbary, Emad, Léo Valon, Marco Fritzsche, Andrew R. Harris, Dale
A. Moulding, Adrian J. Thrasher, Eleanor Stride, L. Mahadevan, and
Guillaume T. Charras. 2013. "The Cytoplasm of Living Cells Behaves as a
Poroelastic Material." *Nature Materials* 12 (3): 253--61.
<https://doi.org/10.1038/nmat3517>.

Mofrad, Mohammad R. K. 2009. "Rheology of the Cytoskeleton." *Annual
Review of Fluid Mechanics* 41 (1): 433--53.
<https://doi.org/10.1146/annurev.fluid.010908.165236>.

Mongera, Alessandro, Marie Pochitaloff, Hannah J. Gustafson, Georgina A.
Stooke-Vaughan, Payam Rowghanian, Sangwoo Kim, and Otger Campàs. 2023.
"Mechanics of the Cellular Microenvironment as Probed by Cells in Vivo
During Zebrafish Presomitic Mesoderm Differentiation." *Nature
Materials* 22 (1): 135--43.
<https://doi.org/10.1038/s41563-022-01433-9>.

Monier, Bruno, Melanie Gettings, Guillaume Gay, Thomas Mangeat, Sonia
Schott, Ana Guarner, and Magali Suzanne. 2015. "Apico-Basal Forces
Exerted by Apoptotic Cells Drive Epithelium Folding." *Nature* 518
(7538): 245--48. <https://doi.org/10.1038/nature14152>.

Morizane, Ryuji, and Joseph V. Bonventre. 2017. "Generation of Nephron
Progenitor Cells and Kidney Organoids from Human Pluripotent Stem
Cells." *Nature Protocols* 12 (1): 195--207.
<https://doi.org/10.1038/nprot.2016.170>.

Mullin, James M., Nicole Agostino, Erika Rendon-Huerta, and James J.
Thornton. 2005. "Keynote Review: Epithelial and Endothelial Barriers in
Human Disease." *Drug Discovery Today* 10 (6): 395--408.
<https://doi.org/10.1016/S1359-6446(05)03379-9>.

Muncie, Jonathon M., Nadia M. E. Ayad, Johnathon N. Lakins, Xufeng Xue,
Jianping Fu, and Valerie M. Weaver. 2020. "Mechanical Tension Promotes
Formation of Gastrulation-like Nodes and Patterns Mesoderm Specification
in Human Embryonic Stem Cells." *Developmental Cell* 55 (6):
679--694.e11. <https://doi.org/10.1016/j.devcel.2020.10.015>.

Munjal, Akankshi, Edouard Hannezo, Tony Y. -C. Tsai, Timothy J.
Mitchison, and Sean G. Megason. 2021. "Extracellular Hyaluronate
Pressure Shaped by Cellular Tethers Drives Tissue Morphogenesis." *Cell*
184 (26): 6313--6325.e18. <https://doi.org/10.1016/j.cell.2021.11.025>.

Murrell, Michael P., and Margaret L. Gardel. 2012. "F-Actin Buckling
Coordinates Contractility and Severing in a Biomimetic Actomyosin
Cortex." *Proceedings of the National Academy of Sciences* 109 (51):
20820--25. <https://doi.org/10.1073/pnas.1214753109>.

Nelson, Celeste M., Jason P. Gleghorn, Mei-Fong Pang, Jacob M. Jaslove,
Katharine Goodwin, Victor D. Varner, Erin Miller, Derek C. Radisky, and
Howard A. Stone. 2017. "Microfluidic Chest Cavities Reveal That
Transmural Pressure Controls the Rate of Lung Development."
*Development* 144 (23): 4328--35. <https://doi.org/10.1242/dev.154823>.

Nelson, Celeste M., Jamie L. Inman, and Mina J. Bissell. 2008.
"Three-Dimensional Lithographically Defined Organotypic Tissue Arrays
for Quantitative Analysis of Morphogenesis and Neoplastic Progression."
*Nature Protocols* 3 (4): 674--78.
<https://doi.org/10.1038/nprot.2008.35>.

Nelson, Celeste M., Ronald P. Jean, John L. Tan, Wendy F. Liu, Nathan J.
Sniadecki, Alexander A. Spector, and Christopher S. Chen. 2005.
"Emergent Patterns of Growth Controlled by Multicellular Form and
Mechanics." *Proceedings of the National Academy of Sciences* 102 (33):
11594--99. <https://doi.org/10.1073/pnas.0502575102>.

Odell, G. M., G. Oster, P. Alberch, and B. Burnside. 1981. "The
Mechanical Basis of Morphogenesis." *Developmental Biology* 85 (2):
446--62. <https://doi.org/10.1016/0012-1606(81)90276-1>.

Okuda, S., N. Takata, Y. Hasegawa, M. Kawada, Y. Inoue, T. Adachi, Y.
Sasai, and M. Eiraku. 2018. "Strain-Triggered Mechanical Feedback in
Self-Organizing Optic-Cup Morphogenesis." *Science Advances* 4 (11):
eaau1354. <https://doi.org/10.1126/sciadv.aau1354>.

Oriola, David, Miquel Marin-Riera, Kerim Anlaş, Nicola Gritti, Marina
Sanaki-Matsumiya, Germaine Aalderink, Miki Ebisuya, James Sharpe, and
Vikas Trivedi. 2022. "Arrested Coalescence of Multicellular Aggregates."
*Soft Matter* 18 (19): 3771--80. <https://doi.org/10.1039/D2SM00063F>.

Osterfield, Miriam, Celeste A. Berg, and Stanislav Y. Shvartsman. 2017.
"Epithelial Patterning, Morphogenesis, and Evolution: Drosophila
Eggshell as a Model." *Developmental Cell* 41 (4): 337--48.
<https://doi.org/10.1016/j.devcel.2017.02.018>.

Ouzeri, Adam, and Marino Arroyo. 2023. "Theory of Multiscale Epithelial
Mechanics Under Stretch: From Active Gels to Vertex Models."

Oyama, Tomoko Gowa, Kotaro Oyama, Hiromi Miyoshi, and Mitsumasa Taguchi.
2021. "3D Cell Sheets Formed via Cell-Driven Buckling-Delamination of
Patterned Thin Films." *Materials & Design* 208 (October): 109975.
<https://doi.org/10.1016/j.matdes.2021.109975>.

Özgüç, Özge, Ludmilla de Plater, Varun Kapoor, Anna Francesca
Tortorelli, Andrew G. Clark, and Jean-Léon Maître. 2022. "Cortical
Softening Elicits Zygotic Contractility During Mouse Preimplantation
Development." *PLOS Biology* 20 (3): e3001593.
<https://doi.org/10.1371/journal.pbio.3001593>.

Pal, Aniket, Vanessa Restrepo, Debkalpa Goswami, and Ramses V. Martinez.
2021. "Exploiting Mechanical Instabilities in Soft Robotics: Control,
Sensing, and Actuation." *Advanced Materials* 33 (19): 2006939.
<https://doi.org/10.1002/adma.202006939>.

Pallarès, Macià Esteve, Irina Pi-Jaumà, Isabela Corina Fortunato,
Valeria Grazu, Manuel Gómez-González, Pere Roca-Cusachs, Jesus M. de la
Fuente, et al. 2022. "Stiffness-Dependent Active Wetting Enables Optimal
Collective Cell Durotaxis." *Nature Physics*, December, 1--11.
<https://doi.org/10.1038/s41567-022-01835-1>.

Palmer, Michael A., Bryan A. Nerger, Katharine Goodwin, Anvitha
Sudhakar, Sandra B. Lemke, Pavithran T. Ravindran, Jared E. Toettcher,
Andrej Košmrlj, and Celeste M. Nelson. 2021. "Stress Ball Morphogenesis:
How the Lizard Builds Its Lung." *Science Advances* 7 (52): eabk0161.
<https://doi.org/10.1126/sciadv.abk0161>.

Palmquist, Karl H., Sydney F. Tiemann, Farrah L. Ezzeddine, Sichen Yang,
Charlotte R. Pfeifer, Anna Erzberger, Alan R. Rodrigues, and Amy E.
Shyer. 2022. "Reciprocal Cell-ECM Dynamics Generate Supracellular
Fluidity Underlying Spontaneous Follicle Patterning." *Cell* 185 (11):
1960--1973.e11. <https://doi.org/10.1016/j.cell.2022.04.023>.

Park, Jin-Ah, Jae Hun Kim, Dapeng Bi, Jennifer A. Mitchel, Nader Taheri
Qazvini, Kelan Tantisira, Chan Young Park, et al. 2015. "Unjamming and
Cell Shape in the Asthmatic Airway Epithelium." *Nature Materials* 14
(10): 1040--48. <https://doi.org/10.1038/nmat4357>.

Pérez-González, Carlos, Ricard Alert, Carles Blanch-Mercader, Manuel
Gómez-González, Tomasz Kolodziej, Elsa Bazellieres, Jaume Casademunt,
and Xavier Trepat. 2019. "Active Wetting of Epithelial Tissues." *Nature
Physics* 15 (1): 79--88. <https://doi.org/10.1038/s41567-018-0279-5>.

Pérez-González, Carlos, Gerardo Ceada, Francesco Greco, Marija Matejčić,
Manuel Gómez-González, Natalia Castro, Anghara Menendez, et al. 2021.
"Mechanical Compartmentalization of the Intestinal Organoid Enables
Crypt Folding and Collective Cell Migration." *Nature Cell Biology* 23
(7): 745--57. <https://doi.org/10.1038/s41556-021-00699-6>.

Popowicz, P., J. Kurzyca, and S. Popowicz. 1986. "'Dome-curve' Three
Size Classes of Domes of MDCK Epithelial Monolayer." *Experimental
Pathology* 29 (3): 147--51.
<https://doi.org/10.1016/S0232-1513(86)80010-X>.

Porazinski, Sean, Huijia Wang, Yoichi Asaoka, Martin Behrndt, Tatsuo
Miyamoto, Hitoshi Morita, Shoji Hata, et al. 2015. "YAP Is Essential for
Tissue Tension to Ensure Vertebrate 3D Body Shape." *Nature* 521 (7551):
217--21. <https://doi.org/10.1038/nature14215>.

Prahl, Louis S., Catherine M. Porter, Jiageng Liu, John M. Viola, and
Alex J. Hughes. 2022. "Independent Control over Cell Patterning and
Adhesion on Hydrogel Substrates for Tissue Interface Mechanobiology."
bioRxiv. <https://doi.org/10.1101/2022.11.16.516785>.

Roca-Cusachs, Pere, Vito Conte, and Xavier Trepat. 2017. "Quantifying
Forces in Cell Biology." *Nature Cell Biology* 19 (7): 742--51.
<https://doi.org/10.1038/ncb3564>.

Salbreux, Guillaume, and Frank Jülicher. 2017. "Mechanics of Active
Surfaces." *Physical Review E* 96 (3): 032404.
<https://doi.org/10.1103/PhysRevE.96.032404>.

Samal, Pinak, Clemens van Blitterswijk, Roman Truckenmüller, and Stefan
Giselbrecht. 2019. "Grow with the Flow: When Morphogenesis Meets
Microfluidics." *Advanced Materials* 31 (17): 1805764.
<https://doi.org/10.1002/adma.201805764>.

Sances, Samuel, Ritchie Ho, Gad Vatine, Dylan West, Alex Laperle, Amanda
Meyer, Marlesa Godoy, et al. 2018. "Human iPSC-Derived Endothelial Cells
and Microengineered Organ-Chip Enhance Neuronal Development." *Stem Cell
Reports* 10 (4): 1222--36.
<https://doi.org/10.1016/j.stemcr.2018.02.012>.

Saw, Thuan Beng, Wang Xi, Benoit Ladoux, and Chwee Teck Lim. 2018.
"Biological Tissues as Active Nematic Liquid Crystals." *Advanced
Materials* 30 (47): 1802579. <https://doi.org/10.1002/adma.201802579>.

Schamberger, B., A. Roschger, R. Ziege, K. Anselme, M. B. Amar, M.
Bykowski, A. P. G. Castro, et al. 2022. "Curvature in Biological
Systems: Its Quantification, Emergence and Implications Across the
Scales." *Advanced Materials*, December, e2206110.

Schliffka, Markus Frederik, and Jean-Léon Maître. 2019. "Stay Hydrated:
Basolateral Fluids Shaping Tissues." *Current Opinion in Genetics &
Development*, Developmental mechanisms, patterning and evolution, 57
(August): 70--77. <https://doi.org/10.1016/j.gde.2019.06.015>.

Schöck, Frieder, and Norbert Perrimon. 2002. "Molecular Mechanisms of
Epithelial Morphogenesis." *Annual Review of Cell and Developmental
Biology* 18 (1): 463--93.
<https://doi.org/10.1146/annurev.cellbio.18.022602.131838>.

Serra-Picamal, Xavier, Vito Conte, Romaric Vincent, Ester Anon,
Dhananjay T. Tambe, Elsa Bazellieres, James P. Butler, Jeffrey J.
Fredberg, and Xavier Trepat. 2012. "Mechanical Waves During Tissue
Expansion." *Nature Physics* 8 (8): 628--34.
<https://doi.org/10.1038/nphys2355>.

Serwane, Friedhelm, Alessandro Mongera, Payam Rowghanian, David A.
Kealhofer, Adam A. Lucio, Zachary M. Hockenbery, and Otger Campàs. 2017.
"In Vivo Quantification of Spatially Varying Mechanical Properties in
Developing Tissues." *Nature Methods* 14 (2): 181--86.
<https://doi.org/10.1038/nmeth.4101>.

Shah, Gopi, Konstantin Thierbach, Benjamin Schmid, Johannes Waschke,
Anna Reade, Mario Hlawitschka, Ingo Roeder, Nico Scherf, and Jan
Huisken. 2019. "Multi-Scale Imaging and Analysis Identify Pan-Embryo
Cell Dynamics of Germlayer Formation in Zebrafish." *Nature
Communications* 10 (1): 5753.
<https://doi.org/10.1038/s41467-019-13625-0>.

Shellard, Adam, and Roberto Mayor. 2021. "Collective Durotaxis Along a
Self-Generated Stiffness Gradient in Vivo." *Nature* 600 (7890):
690--94. <https://doi.org/10.1038/s41586-021-04210-x>.

Shyer, Amy E., Alan R. Rodrigues, Grant G. Schroeder, Elena Kassianidou,
Sanjay Kumar, and Richard M. Harland. 2017. "Emergent Cellular
Self-Organization and Mechanosensation Initiate Follicle Pattern in the
Avian Skin." *Science* 357 (6353): 811--15.
<https://doi.org/10.1126/science.aai7868>.

Shyer, Amy E., Tuomas Tallinen, Nandan L. Nerurkar, Zhiyan Wei, Eun Seok
Gil, David L. Kaplan, Clifford J. Tabin, and L. Mahadevan. 2013.
"Villification: How the Gut Gets Its Villi." *Science* 342 (6155):
212--18. <https://doi.org/10.1126/science.1238842>.

Sidhaye, Jaydeep, and Caren Norden. 2017. "Concerted Action of
Neuroepithelial Basal Shrinkage and Active Epithelial Migration Ensures
Efficient Optic Cup Morphogenesis." Edited by Didier YR Stainier.
*eLife* 6 (April): e22689. <https://doi.org/10.7554/eLife.22689>.

Sollier, Elodie, Coleman Murray, Pietro Maoddi, and Dino Di Carlo. 2011.
"Rapid Prototyping Polymers for Microfluidic Devices and High Pressure
Injections." *Lab on a Chip* 11 (22): 3752--65.
<https://doi.org/10.1039/C1LC20514E>.

Stanton, Alice E., Xinming Tong, and Fan Yang. 2019. "Extracellular
Matrix Type Modulates Mechanotransduction of Stem Cells." *Acta
Biomaterialia* 96 (September): 310--20.
<https://doi.org/10.1016/j.actbio.2019.06.048>.

Stokkermans, Anniek, Aditi Chakrabarti, Kaushikaram Subramanian, Ling
Wang, Sifan Yin, Prachiti Moghe, Petrus Steenbergen, et al. 2022.
"Muscular Hydraulics Drive Larva-Polyp Morphogenesis." *Current Biology*
32 (21): 4707--4718.e8. <https://doi.org/10.1016/j.cub.2022.08.065>.

Stokkermans, Anniek, Aditi Chakrabarti, Ling Wang, Prachiti Moghe,
Kaushikaram Subramanian, Petrus Steenbergen, Gregor Mönke, et al. 2021.
"Ethology of Morphogenesis Reveals the Design Principles of Cnidarian
Size and Shape Development." Cold Spring Harbor Laboratory.
<https://doi.org/10.1101/2021.08.19.456976>.

Sui, Liyuan, Silvanus Alt, Martin Weigert, Natalie Dye, Suzanne Eaton,
Florian Jug, Eugene W. Myers, Frank Jülicher, Guillaume Salbreux, and
Christian Dahmann. 2018. "Differential Lateral and Basal Tension Drive
Folding of Drosophila Wing Discs Through Two Distinct Mechanisms."
*Nature Communications* 9 (1): 4620.
<https://doi.org/10.1038/s41467-018-06497-3>.

Sunyer, Raimon, Vito Conte, Jorge Escribano, Alberto Elosegui-Artola,
Anna Labernadie, Léo Valon, Daniel Navajas, et al. 2016. "Collective
Cell Durotaxis Emerges from Long-Range Intercellular Force
Transmission." *Science* 353 (6304): 1157--61.
<https://doi.org/10.1126/science.aaf7119>.

Syed, Zulfeqhar A., Anne-Laure Bougé, Sunitha Byri, Tina M. Chavoshi,
Erika Tång, Hervé Bouhin, Iris F. van Dijk-Härd, and Anne Uv. 2012. "A
Luminal Glycoprotein Drives Dose-Dependent Diameter Expansion of the
Drosophila Melanogaster Hindgut Tube." *PLOS Genetics* 8 (8): e1002850.
<https://doi.org/10.1371/journal.pgen.1002850>.

Tallinen, Tuomas, Jun Young Chung, François Rousseau, Nadine Girard,
Julien Lefèvre, and L. Mahadevan. 2016. "On the Growth and Form of
Cortical Convolutions." *Nature Physics* 12 (6): 588--93.
<https://doi.org/10.1038/nphys3632>.

Tambe, Dhananjay T., C. Corey Hardin, Thomas E. Angelini, Kavitha
Rajendran, Chan Young Park, Xavier Serra-Picamal, Enhua H. Zhou, et al.
2011. "Collective Cell Guidance by Cooperative Intercellular Forces."
*Nature Materials* 10 (6): 469--75. <https://doi.org/10.1038/nmat3025>.

Tang, Wenhui, Amit Das, Adrian F. Pegoraro, Yu Long Han, Jessie Huang,
David A. Roberts, Haiqian Yang, et al. 2022. "Collective Curvature
Sensing and Fluidity in Three-Dimensional Multicellular Systems."
*Nature Physics* 18 (11): 1371--78.
<https://doi.org/10.1038/s41567-022-01747-0>.

Tanner, C., D. A. Frambach, and D. S. Misfeldt. 1983. "Transepithelial
Transport in Cell Culture. A Theoretical and Experimental Analysis of
the Biophysical Properties of Domes." *Biophysical Journal* 43 (2):
183--90. <https://doi.org/10.1016/S0006-3495(83)84339-2>.

"The 100-Year-Old Challenge to Darwin That Is Still Making Waves in
Research." 2017. *Nature* 544 (7649): 138--39.
<https://doi.org/10.1038/544138a>.

Thiery, Jean Paul, Hervé Acloque, Ruby Y. J. Huang, and M. Angela Nieto.
2009. "Epithelial-Mesenchymal Transitions in Development and Disease."
*Cell* 139 (5): 871--90. <https://doi.org/10.1016/j.cell.2009.11.007>.

Thompson, D'Arcy Wentworth. 1979. *On Growth and Form*. Repr. Cambridge:
Univ. Pr.

Tlili, Sham, Estelle Gauquelin, Brigitte Li, Olivier Cardoso, Benoît
Ladoux, Hélène Delanoë-Ayari, and François Graner. 2018. "Collective
Cell Migration Without Proliferation: Density Determines Cell Velocity
and Wave Velocity." *Royal Society Open Science* 5 (5): 172421.
<https://doi.org/10.1098/rsos.172421>.

Tomba, Caterina, Valeriy Luchnikov, Luca Barberi, Carles
Blanch-Mercader, and Aurélien Roux. 2022. "Epithelial Cells Adapt to
Curvature Induction via Transient Active Osmotic Swelling."
*Developmental Cell* 57 (10): 1257--1270.e5.
<https://doi.org/10.1016/j.devcel.2022.04.017>.

Torras, Núria, María García-Díaz, Vanesa Fernández-Majada, and Elena
Martínez. 2018. "Mimicking Epithelial Tissues in Three-Dimensional Cell
Culture Models." *Frontiers in Bioengineering and Biotechnology* 6.

Torres-Sánchez, Alejandro, Max Kerr Winter, and Guillaume Salbreux.
2021. "Tissue Hydraulics: Physics of Lumen Formation and Interaction."
*Cells & Development*, Quantitative Cell and Developmental Biology, 168
(December): 203724. <https://doi.org/10.1016/j.cdev.2021.203724>.

Trentesaux, Coralie, Toshimichi Yamada, Ophir D. Klein, and Wendell A.
Lim. 2023. "Harnessing Synthetic Biology to Engineer Organoids and
Tissues." *Cell Stem Cell* 30 (1): 10--19.
<https://doi.org/10.1016/j.stem.2022.12.013>.

Trepat, Xavier, and Erik Sahai. 2018. "Mesoscale Physical Principles of
Collective Cell Organization." *Nature Physics* 14 (7): 671--82.
<https://doi.org/10.1038/s41567-018-0194-9>.

Trushko, Anastasiya, Ilaria Di Meglio, Aziza Merzouki, Carles
Blanch-Mercader, Shada Abuhattum, Jochen Guck, Kevin Alessandri, et al.
2020. "Buckling of an Epithelium Growing Under Spherical Confinement."
*Developmental Cell* 54 (5): 655--668.e6.
<https://doi.org/10.1016/j.devcel.2020.07.019>.

Valentich, J. D., R. Tchao, and J. Leighton. 1979. "Hemicyst Formation
Stimulated by Cyclic AMP in Dog Kidney Cell Line MDCK." *Journal of
Cellular Physiology* 100 (2): 291--304.
<https://doi.org/10.1002/jcp.1041000210>.

Valet, Manon, Eric D. Siggia, and Ali H. Brivanlou. 2022. "Mechanical
Regulation of Early Vertebrate Embryogenesis." *Nature Reviews Molecular
Cell Biology* 23 (3): 169--84.
<https://doi.org/10.1038/s41580-021-00424-z>.

Valon, Léo, Ariadna Marín-Llauradó, Thomas Wyatt, Guillaume Charras, and
Xavier Trepat. 2017. "Optogenetic Control of Cellular Forces and
Mechanotransduction." *Nature Communications* 8 (1): 14396.
<https://doi.org/10.1038/ncomms14396>.

Varner, Victor D., Jason P. Gleghorn, Erin Miller, Derek C. Radisky, and
Celeste M. Nelson. 2015. "Mechanically Patterning the Embryonic Airway
Epithelium." *Proceedings of the National Academy of Sciences* 112 (30):
9230--35. <https://doi.org/10.1073/pnas.1504102112>.

Vedula, Sri Ram Krishna, Man Chun Leong, Tan Lei Lai, Pascal Hersen,
Alexandre J. Kabla, Chwee Teck Lim, and Benoît Ladoux. 2012. "Emerging
Modes of Collective Cell Migration Induced by Geometrical Constraints."
*Proceedings of the National Academy of Sciences* 109 (32): 12974--79.
<https://doi.org/10.1073/pnas.1119313109>.

Veenvliet, Jesse V., Pierre-François Lenne, David A. Turner, Iftach
Nachman, and Vikas Trivedi. 2021. "Sculpting with Stem Cells: How Models
of Embryo Development Take Shape." *Development* 148 (24): dev192914.
<https://doi.org/10.1242/dev.192914>.

Venturini, Valeria, Fabio Pezzano, Frederic Català Castro, Hanna-Maria
Häkkinen, Senda Jiménez-Delgado, Mariona Colomer-Rosell, Monica Marro,
et al. 2020. "The Nucleus Measures Shape Changes for Cellular
Proprioception to Control Dynamic Cell Behavior." *Science* 370 (6514):
eaba2644. <https://doi.org/10.1126/science.aba2644>.

Vianello, Stefano, and Matthias P. Lutolf. 2019. "Understanding the
Mechanobiology of Early Mammalian Development Through Bioengineered
Models." *Developmental Cell* 48 (6): 751--63.
<https://doi.org/10.1016/j.devcel.2019.02.024>.

Vignaud, Timothée, Laurent Blanchoin, and Manuel Théry. 2012. "Directed
Cytoskeleton Self-Organization." *Trends in Cell Biology*, Special Issue
Synthetic Cell Biology, 22 (12): 671--82.
<https://doi.org/10.1016/j.tcb.2012.08.012>.

Virchow, Rudolf, Frank Chance, John Goodsir, King's College London, and
Pathological Institute of Berlin. 1860. *Cellular Pathology as Based
Upon Physiological and Pathological Histology; Twenty Lectures Delivered
in the Pathological Institute of Berlin During the Months of February,
March, and April, 1858*. London: John Churchill.
<https://doi.org/10.5962/bhl.title.110759>.

Voss-Böhme, Anja. 2012. "Multi-Scale Modeling in Morphogenesis: A
Critical Analysis of the Cellular Potts Model." *PLOS ONE* 7 (9):
e42852. <https://doi.org/10.1371/journal.pone.0042852>.

Wagh, Kaustubh, Momoko Ishikawa, David A. Garcia, Diana A. Stavreva,
Arpita Upadhyaya, and Gordon L. Hager. 2021. "Mechanical Regulation of
Transcription: Recent Advances." *Trends in Cell Biology* 31 (6):
457--72. <https://doi.org/10.1016/j.tcb.2021.02.008>.

Walma, David A. Cruz, and Kenneth M. Yamada. 2020. "The Extracellular
Matrix in Development." *Development* 147 (10): dev175596.
<https://doi.org/10.1242/dev.175596>.

Wang, Yanzhong, and Jin Qian. 2019. "Buckling of Filamentous Actin
Bundles in Filopodial Protrusions." *Acta Mechanica Sinica* 35 (2):
365--75. <https://doi.org/10.1007/s10409-019-00838-1>.

Warmflash, Aryeh, Benoit Sorre, Fred Etoc, Eric D. Siggia, and Ali H.
Brivanlou. 2014. "A Method to Recapitulate Early Embryonic Spatial
Patterning in Human Embryonic Stem Cells." *Nature Methods* 11 (8):
847--54. <https://doi.org/10.1038/nmeth.3016>.

Waters, Christopher M., Esra Roan, and Daniel Navajas. 2012.
"Mechanobiology in Lung Epithelial Cells: Measurements, Perturbations,
and Responses." *Comprehensive Physiology* 2 (1): 1--29.
<https://doi.org/10.1002/cphy.c100090>.

Wen, Qi, and Paul A. Janmey. 2011. "Polymer Physics of the
Cytoskeleton." *Current Opinion in Solid State and Materials Science* 15
(5): 177--82. <https://doi.org/10.1016/j.cossms.2011.05.002>.

Wensink, Henricus H., Jörn Dunkel, Sebastian Heidenreich, Knut Drescher,
Raymond E. Goldstein, Hartmut Löwen, and Julia M. Yeomans. 2012.
"Meso-Scale Turbulence in Living Fluids." *Proceedings of the National
Academy of Sciences* 109 (36): 14308--13.
<https://doi.org/10.1073/pnas.1202032109>.

Wolfram, Stephen. 2017. "The Scientist Who Cracked Biological Mysteries
With Math \| Backchannel." *Wired*.

Wright, Nicholas A, and Richard Poulsom. 2012. "Omnis Cellula e Cellula
Revisited: Cell Biology as the Foundation of Pathology." *The Journal of
Pathology* 226 (2): 145--47. <https://doi.org/10.1002/path.3030>.

Wyatt, Tom P. J., Jonathan Fouchard, Ana Lisica, Nargess Khalilgharibi,
Buzz Baum, Pierre Recho, Alexandre J. Kabla, and Guillaume T. Charras.
2020. "Actomyosin Controls Planarity and Folding of Epithelia in
Response to Compression." *Nature Materials* 19 (1): 109--17.
<https://doi.org/10.1038/s41563-019-0461-x>.

Wyatt, Tom P. J., Andrew R. Harris, Maxine Lam, Qian Cheng, Julien
Bellis, Andrea Dimitracopoulos, Alexandre J. Kabla, Guillaume T.
Charras, and Buzz Baum. 2015. "Emergence of Homeostatic Epithelial
Packing and Stress Dissipation Through Divisions Oriented Along the Long
Cell Axis." *Proceedings of the National Academy of Sciences* 112 (18):
5726--31. <https://doi.org/10.1073/pnas.1420585112>.

Wyatt, Tom, Buzz Baum, and Guillaume Charras. 2016. "A Question of Time:
Tissue Adaptation to Mechanical Forces." *Current Opinion in Cell
Biology*, Cell architecture, 38 (February): 68--73.
<https://doi.org/10.1016/j.ceb.2016.02.012>.

Xi, Wang, Thuan Beng Saw, Delphine Delacour, Chwee Teck Lim, and Benoit
Ladoux. 2018. "Material Approaches to Active Tissue Mechanics." *Nature
Reviews Materials* 4 (1): 23--44.
<https://doi.org/10.1038/s41578-018-0066-z>.

Yeung, Tony, Penelope C. Georges, Lisa A. Flanagan, Beatrice Marg,
Miguelina Ortiz, Makoto Funaki, Nastaran Zahir, Wenyu Ming, Valerie
Weaver, and Paul A. Janmey. 2005. "Effects of Substrate Stiffness on
Cell Morphology, Cytoskeletal Structure, and Adhesion." *Cell Motility*
60 (1): 24--34. <https://doi.org/10.1002/cm.20041>.

Yevick, Hannah G., Pearson W. Miller, Jörn Dunkel, and Adam C. Martin.
2019. "Structural Redundancy in Supracellular Actomyosin Networks
Enables Robust Tissue Folding." *Developmental Cell* 50 (5):
586--598.e3. <https://doi.org/10.1016/j.devcel.2019.06.015>.

Yu, Jessica C, and Rodrigo Fernandez-Gonzalez. 2016. "Local Mechanical
Forces Promote Polarized Junctional Assembly and Axis Elongation in
Drosophila." Edited by John B Wallingford. *eLife* 5 (January): e10757.
<https://doi.org/10.7554/eLife.10757>.

Zampieri, Fabio, Matteo Coen, and Giulio Gabbiani. 2014. "The Prehistory
of the Cytoskeleton Concept." *Cytoskeleton* 71 (8): 464--71.
<https://doi.org/10.1002/cm.21177>.

Zhang, Liucheng, Yi Xiang, Hongbo Zhang, Liying Cheng, Xiyuan Mao, Ning
An, Lu Zhang, et al. 2020. "A Biomimetic 3D-Self-Forming Approach for
Microvascular Scaffolds." *Advanced Science* 7 (9): 1903553.
<https://doi.org/10.1002/advs.201903553>.

[^1]: Ruysch is referred to as a "Artist of death" because of his famous
    anatomical collection. He was the first to use arterial embalming,
    which allowed for visualizing and dissecting smallest arteries. He
    also was part of the macabre practice of public dissections (Halley
    2019).

[^2]: Finding a fundamental unit of living entities comes from the
    philosophy of Gottfried W. Leibniz. It was based on the idea of
    "monad". Thanks to progress in microscopy and philosophy,
    naturalists were able to put together ideas for cells, fibers, and
    even cytoskeleton!(Zampieri, Coen, and Gabbiani 2014)

[^3]: The famous epigram was coined by François-Vincent Raspail. Virchow
    is regarded as influential biomedical scientist of 19th century, but
    more interesting part is as a radical who took part in the March
    revolution of 1848. He was one of the first to advocate for the
    social origins of illness (Wright and Poulsom 2012; Brown and Fee
    2006).

[^4]: Funnily, He criticized the zoologists and morphologists of the
    time of assigning shapes to psychical instinct of the organism or
    some divine interference for creating the perfect shapes: "He finds
    a simple geometric construction, for instance in the honeycomb
    structure, he would fain refer it to psychical instinct or design
    rather than in the operation of physical forces. \... When he sees
    in snail, or nautilus, or tiny foraminiferal or radiolarian shell a
    close approach to sphere or spiral, he is prone of old habit to
    believe that after all it is something more than a spiral or a
    sphere, and that in this \"something more\" there lies what neither
    mathematics nor physics can explain

[^5]: \"we recognize the appearance of a \"froth,\" precisely resembling
    that which we can construct by imprisoning a mass of soap-bubbles in
    a narrow vessel with flat sides of glass; in both cases we see the
    cell-walls everywhere meeting, by threes, at angles of $120\deg$,
    irrespective of the size of the individual cells: whose relative
    size, on the other hand, determines the curvature of the
    partition-walls\", writes Thompson

[^6]: Matthew Good's commentary provides an insightful perspective on
    the complexity involved in building cells from interacting
    molecules. Meanwhile, Xavier Trepat argues that a bottom-up approach
    does not fully explain the emergent behavior of higher-level
    structures and emphasizes the need for constructing tissues at the
    mesoscale. Trepat uses the analogy of traffic jams to illustrate the
    importance of considering the collective behavior of cells in tissue
    engineering (Good and Trepat 2018).

[^7]: . Thompson writes,'\...to seek not for ends but for antecedents is
    the way of the physicists, who finds causes in what he has learned
    to recognize as fundamental properties, or inseparable concomitants,
    or unchanging laws, of matter and of energy." (Thompson 1979)

[^8]: \"Mechanical instabilities have provided a unique approach to
    imbue "material intelligence" into soft machines without requiring
    the addition of rigid components. For example, binary actuators
    relying on mechanical instabilities can recreate logic modules and
    reproduce valving functionality using entirely soft elements.

[^9]: I cannot recommend enough the chapter "the forms of cell". He
    states "Many forms are capable of realization under surface-tension,
    ... The subject is a very general one; it is, in its essence, more
    mathematical than physical; it is part of the mathematics of
    surfaces, and only comes into relation with surface-tension because
    this physical phenomenon illustrates and exemplifies, in a concrete
    way, the simple and symmetrical conditions with which the
    mathematical theory is capable of dealing."

[^10]: It is very important to acknowledge the contribution of
    Madin-Darby canine kidney (MDCK) cells to the field of
    mechanobiology and enhancing our understanding of tissues *in
    vitro*. Stewart H. Madin and Norman B. Darby, Jr. isolated female
    cocker spaniel dog's kidney tubules cells in 1958. MDCK cells can
    self-organize in 2D and 3D; form monolayers and stratified layers;
    and undergo collective migrations. These cells are incredibly robust
    for experimentation.

[^11]: Metric tensor, a mathematical object used in differential
    geometry, can be used to measure distances, angles, and volumes in
    curved spaces. Here, it is measuring the cortical surface.
