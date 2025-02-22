# Assortative mixing in micro-architecturally annotated brain connectomes

This repository contains scripts and functions to reproduce the results presented in [Assortative mixing in micro-architecturally annotated brain connectomes](https://doi.org/10.1038/s41467-023-38585-4).

## The main script

[main_script.py](main_script.py) contains a script that allows anyone to replicate the analysis described in the paper by simply running it. This script uses functions stored in [functions.py](functions.py) to load the required data, run the analyses and plot the figures presented in the paper.

A user can load its own data and modify this main script accordingly to reproduce similar analyses using their own dataset.

## The data

The [data](data) folder contains the data that was used to perform the analysis described in the main text of the paper. This data is stored in dictionaries saved as `.pickle` files. See the *Methods* section of the paper for more information about the data. **Before using this data, please refer to the relevant publications listed in the references section below for more information about the data terms associated with each dataset.**

###  human_FC

Dictionary storing relevant connectivity data for the human functional connectome. This dictionary contains:

- `adj`: adjacency matrix of the functional connectome used in the main text, which was reconstructed from HCP data (Van Essen et al., 2013) and parcellated using the 800 nodes [Schaefer parcellation](https://github.com/ThomasYeoLab/CBIG/tree/master/stable_projects/brain_parcellation/Schaefer2018_LocalGlobal) (Schaefer et al., 2018). See Park et al. (2021) for more information about the processing.
- `coords`: coordinates of the nodes in the Schaefer parcellation.
- `dist`: Euclidean distance between the nodes in the Schaefer parcellation.
- `EI_ratio`: Ratio between the mean density of excitatory receptors and the mean density of inhibitory receptors in each parcel. See below for more information about the receptor density dataset.
- `genePC1`: Principal axis of transcriptional variation across the human cortex. Transcriptional data was obtained from the Allen Human Brain Atlas (Hawrylycz et al., 2012), and pre-processed using [abagen](https://github.com/rmarkello/abagen) (Markello et al., 2021).
- `receptor_den`: Receptor density in each parcel, averaged across 18 receptors and transporters. See below for more information about the receptor density dataset.
- `t1t2`: Mean T1w/T2w ratio in each parcel. extracted from the HCP dataset.
- `thi`: Mean cortical thickness of each parcel, extracted from the HCP dataset.
- `spin_nulls`: Spatial aucorrelation-presserving permutations generated using [neuromaps](https://github.com/netneurolab/neuromaps) (Markello et al., 2022)

### human_FC_s400

Dictionary storing relevant connectivity data for the human functional connectome
generated using the 400 nodes Schaefer parcellation (supplementary results).
This dictionary contains the same entries as `human_FC`.

### human_FC_L

Dictionary storing relevant connectivity data for the left hemipshere of the human functional connectome (supplementary results). This dictionary contains the same entries as `human_FC`.

### human_FC_219

Dictionary storing relevant connectivity data for the group-averaged human functional connectome generated from the [Lausanne dataset](https://zenodo.org/record/2872624#.Y_kkTHbMJD8), using the 219 nodes Cammoun atlas (Cammoun et al., 2012) (supplementary results). This dictionary contains the same entries as `human_FC`.

### human_FC_1000

Dictionary storing relevant connectivity data for the group-averaged human functional connectome generated from the [Lausanne dataset](https://zenodo.org/record/2872624#.Y_kkTHbMJD8), using the 1000 nodes Cammoun atlas (Cammoun et al., 2012) (supplementary results). This dictionary contains the same entries as `human_SC`. Note: Due to file size issues, we only provide 5000 of the 10000 null permutations.

### human_SC

Dictionary storing relevant connectivity data for the human structural connectome. This dictionary contains:

- `adj`: adjacency matrix of the structural connectome used in the main text, which was reconstructed from HCP data (Van Essen et al., 2013) and parcellated using the 800 nodes [Schaefer parcellation](https://github.com/ThomasYeoLab/CBIG/tree/master/stable_projects/brain_parcellation/Schaefer2018_LocalGlobal) (Schaefer et al., 2018). See Park et al. (2021) for more information about the processing.
- `coords`: coordinates of the nodes in the Schaefer parcellation.
- `dist`: Euclidean distance between the nodes in the Schaefer parcellation.
- `EI_ratio`: Ratio between the mean density of excitatory receptors and the mean density of inhibitory receptors in each parcel. See below for more information about the receptor density dataset.
- `genePC1`: Principal axis of transcriptional variation across the human cortex. Transcriptional data was obtained from the Allen Human Brain Atlas (Hawrylycz et al., 2012), and pre-processed using [abagen](https://github.com/rmarkello/abagen) (Markello et al., 2021).
- `receptor_den`: Receptor density in each parcel, averaged across 18 receptors and transporters. See below for more information about the receptor density dataset.
- `t1t2`: Mean T1w/T2w ratio in each parcel. extracted from the HCP dataset.
- `thi`: Mean cortical thickness of each parcel, extracted from the HCP dataset.
- `ci`: Communities of the structural connectome
- `spin_nulls`: Spatial aucorrelation-presserving permutations generated using [neuromaps](https://github.com/netneurolab/neuromaps) (Markello et al., 2022)
- `noplot`: List of names in lhannot and rhannot to not plot. This list is used by the 'netneurotools.plotting.plot_fsaverage' function.
- `order`: Order of the hemispheres in the parcellation (either 'LR' or 'RL'). This order is used by the 'netneurotools.plotting.plot_fsaverage' function.
-`geo_dist_L` and `geo_dist_R`: Geodesic distance between each parcel of the Schaefer atlas for the left (L) and for the right (R) hemispheres.
-`hemiid`: Label, for each parcel, indicating whether it is located in the left or the right hemisphere

### human_SC_s400

Dictionary storing relevant connectivity data for the human structural connectome generated using the 400 nodes Schaefer parcellation (supplementary results). This dictionary contains the same entries as `human_SC`.

### human_SC_L

Dictionary storing relevant connectivity data for the left hemipshere of the human structural connectome (supplementary results). This dictionary contains the same entries as `human_SC`.

### human_SC_219

Dictionary storing relevant connectivity data for the group-averaged human structural connectome generated from the [Lausanne dataset](https://zenodo.org/record/2872624#.Y_kkTHbMJD8), using the 219 nodes Cammoun atlas (Cammoun et al., 2012) (supplementary results). This dictionary contains the same entries as `human_SC`.

### human_SC_1000

Dictionary storing relevant connectivity data for the group-averaged human structural connectome generated from the [Lausanne dataset](https://zenodo.org/record/2872624#.Y_kkTHbMJD8), using the 1000 nodes Cammoun atlas (Cammoun et al., 2012) (supplementary results). This dictionary contains the same entries as `human_SC`. Note: Due to file size issues, we only provide 5000 of the 10000 null permutations.

### human_SC_nolog

Dictionary storing relevant connectivity data for the human structural connectome, with the original weights of the connectome (not log-transformed). This dictionary contains the same entries as `human_SC`.

### mouse_oh

Dictionary storing relevant connectivity data for the mouse (oh2014) connectome. This dictionary contains:

- `adj`: adjacency matrix of the oh2014 connectome. This connectome was generated by Oh et al. (2014) using data from the Allen Mouse Brain Connectivity Atlas.
- `coords`: coordinates of each region of the oh2014 connectome. They were obtained from the Allen Mouse Reference Atlas, version 2 (2011)
- `dist`: Euclidean distance between each region of the oh2014 connectome.
- `genePC1`: principal axis of gene expression variation, computed using data from the Allen Mouse Brain Atlas.

### macaque_scholtens

Dictionary storing relevant connectivity data for the mouse (scholtens2014) connectome. This dictionary contains:

- `adj`: adjacency matrix of the scholtens2014 connectome. This connectome was generated by Scholtens et al. (2014) using data from the CoCoMac database (Stephan et al., 2001). The parcellation used for the network reconstruction is an hybrid between the Walker-von Bonin and Bailey atlases and contains 39 non-overlapping cortical regions.
- `coords`: coordinates of each region in scholtens2014 connectome
- `dist`: Euclidean distance between each region of the scholtens connectome.
- `neuron_den`: neuron density information extracted from brain tissues of an Old World macaque monkey (Collins et al., 2010)
- `t1t2`: T1w/T2w information obtained from the structural MRI scans of 19 adult macaques (Donahue et al., 2016). The original, unparcellated, data is [available on Balsa](https://balsa.wustl.edu/study/show/W336)
- `thi`: cortical thickness information obtained from the structural MRI scans of 19 adult macaques (Donahue et al., 2016). The original, unparcellated, data is [available on Balsa](https://balsa.wustl.edu/study/show/W336)

### laminar_thicknesses

- `data`: Parcellated brain maps of laminar thickness for each of the six cortical layers of the Merkel-stained BigBrain histological atlas (Amunts et al., 2013, Wagstyl et al., 2020). The data was downloaded through the [FTP site of the BigBrain Project](https://ftp.bigbrainproject.org/). Each column represent a different brain map.
- `names`: List of names identifying the layers associated with each row of the 'data' matrix.

### receptor_densities

- `data`: Parcellated brain maps of the receptor densities for 18 different neurotrasmitter receptors and transporters (Hansen et al., 2021). Each column represent a different brain map.
- `names`: List of names identifying the receptor or transporter associated with each row of the 'data' matrix.

### neurosynth

- `data`: Parcellated brain maps of probabilistic association between functional key words and individual parcels, generated using [neurosynth](https://neurosynth.org/) (Yarkoni et al., 2011). Each column represent a different brain map.
- `names`: List of terms identifiying each row of the 'data' matrix.

### burt nulls

This folder contains null annotations preserving the spatial auto-correlation of each annotation, for each species. These null annotations were generated according to the method proposed in Burt et al. (2020), and using the [brainSMASH software](https://github.com/murraylab/brainsmash) introduced in the same paper.

## The results

The [results](results) folder contains the main results of the experiments presented in the paper. These results are already pre-computed, and can be re-computed using [main_script.py](main_script.py). For more information about the results, see the *Results* section of the paper.

## The requirements

The experiments presented in this repository make use of a certain number of python packages that will be necessary to run the main script. These packages are:

- [brainspace](<https://github.com/MICA-MNI/BrainSpace>): Toolbox that allows for the identification and analysis of gradients from neuroimaging and connectomic datasets. Used here to generate spatial autocorrelation-preseving null annotations using Moran Spectral Randomization.
- [netneurotools](<https://github.com/netneurolab/netneurotools>) : Netneurotools is a collection of functions written in Python that get frequent usage in the Network Neuroscience Lab.
- [palettable](<https://github.com/jiffyclub/palettable>) : A library of color palettes for python.
- [numpy](<https://numpy.org/doc/stable/reference/>)
- [scipy](<https://docs.scipy.org/doc/scipy/reference/>)
- [tqdm](<https://github.com/tqdm/tqdm>)
- [matplotlib](<https://matplotlib.org/>)
- [seaborn](<https://seaborn.pydata.org/index.html>)

## The references

**Human Connectome Project (HCP)**

*data acquisition*: Van Essen, D. C., Smith, S. M., Barch, D. M., Behrens, T. E., Yacoub, E., Ugurbil, K., & Wu-Minn HCP Consortium. (2013). The WU-Minn human connectome project: an overview. Neuroimage, 80, 62-79.

*data processing*: Park, B. Y., de Wael, R. V., Paquola, C., Larivière, S., Benkarim, O., Royer, J., ... & Bernhardt, B. C. (2021). Signal diffusion along connectome gradients and inter-hub routing differentially contribute to dynamic human brain function. Neuroimage, 224, 117429.

**Lausanne Connectome Dataset**
Griffa, A., Alemán-Gómez, Y., and Hagmann, P. (2019). Structural and functional connectome from 70 young healthy adults. doi:10.5281/zenodo.2872624. type: dataset.

**Schaefer atlas**

Schaefer, A., Kong, R., Gordon, E. M., Laumann, T. O., Zuo, X. N., Holmes, A. J., ... & Yeo, B. T. (2018). Local-global parcellation of the human cerebral cortex from intrinsic functional connectivity MRI. Cerebral cortex, 28(9), 3095-3114.

**Cammoun atlas**

Cammoun, L., Gigandet, X., Meskaldji, D., Thiran, J. P., Sporns, O., Do, K. Q., Maeder, P., Meuli, R., and Hagmann, P. (2012). Mapping the human connectome at multiple scales with diffusion spectrum MRI. Journal of Neuroscience Methods, 203(2):386–397.

**Allen Human Brain Atlas**

*data acquisition*: Hawrylycz, M. J., Lein, E. S., Guillozet-Bongaarts, A. L., Shen, E. H., Ng, L., Miller, J. A., ... & Jones, A. R. (2012). An anatomically comprehensive atlas of the adult human brain transcriptome. Nature, 489(7416), 391-399.

*data pre-processing*: Markello, R. D., Arnatkeviciute, A., Poline, J. B., Fulcher, B. D., Fornito, A., & Misic, B. (2021). Standardizing workflows in imaging transcriptomics with the abagen toolbox. Elife, 10, e72129.

**neuromaps**

Markello, R. D., Hansen, J. Y., Liu, Z. Q., Bazinet, V., Shafiei, G., Suarez, L. E., ... & Misic, B. (2022). Neuromaps: structural and functional interpretation of brain maps. bioRxiv.

**Allen Mouse Brain Connectivity Atlas**

Oh, S. W., Harris, J. A., Ng, L., Winslow, B., Cain, N., Mihalas, S., ... & Zeng, H. (2014). A mesoscale connectome of the mouse brain. Nature, 508(7495), 207-214.

**Allen Mouse Brain Atlas**

Lein, E. S., Hawrylycz, M. J., Ao, N., Ayres, M., Bensinger, A., Bernard, A., ... & Jones, A. R. (2007). Genome-wide atlas of gene expression in the adult mouse brain. Nature, 445(7124), 168-176.

**CoCoMac database**

*database*: Stephan, K. E., Kamper, L., Bozkurt, A., Burns, G. A., Young, M. P., & Kötter, R. (2001). Advanced database methodology for the Collation of Connectivity data on the Macaque brain (CoCoMac). Philosophical Transactions of the Royal Society of London. Series B: Biological Sciences, 356(1412), 1159-1186.

*connectome*: Scholtens, L. H., Schmidt, R., de Reus, M. A., & van den Heuvel, M. P. (2014). Linking macroscale graph analytical organization to microscale neuroarchitectonics in the macaque connectome. Journal of Neuroscience, 34(36), 12192-12205.

**Neuron density (macaque)**

Collins, C. E., Airey, D. C., Young, N. A., Leitch, D. B., & Kaas, J. H. (2010). Neuron densities vary across and within cortical areas in primates. Proceedings of the National Academy of Sciences, 107(36), 15927-15932.

**Macaque structural MRI scans**

Donahue, C. J., Sotiropoulos, S. N., Jbabdi, S., Hernandez-Fernandez, M., Behrens, T. E., Dyrby, T. B., ... & Glasser, M. F. (2016). Using diffusion tractography to predict cortical connection strength and distance: a quantitative comparison with tracers in the monkey. Journal of Neuroscience, 36(25), 6758-6770.

**BigBrain Atlas**

*original atlas*: Amunts, K., Lepage, C., Borgeat, L., Mohlberg, H., Dickscheid, T., Rousseau, M. É., ... & Evans, A. C. (2013). BigBrain: an ultrahigh-resolution 3D human brain model. Science, 340(6139), 1472-1475.

*laminar segmentation*: Wagstyl, K., Larocque, S., Cucurull, G., Lepage, C., Cohen, J. P., Bludau, S., ... & Evans, A. C. (2020). BigBrain 3D atlas of cortical layers: cortical and laminar thickness gradients diverge in sensory and motor cortices. PLoS biology, 18(4), e3000678.

**Receptor density atlas**

Hansen, J. Y., Shafiei, G., Markello, R. D., Smart, K., Cox, S. M., Wu, Y., ... & Misic, B. (2021). Mapping neurotransmitter systems to the structural and functional organization of the human neocortex. Biorxiv.

**Neurosynth**

Yarkoni, T., Poldrack, R. A., Nichols, T. E., Van Essen, D. C., & Wager, T. D. (2011). Large-scale automated synthesis of human functional neuroimaging data. Nature methods, 8(8), 665-670.

**Burt nulls (Brain surrogates with autocorrelated spatial heterogeneity)**

Burt, J.B., Helmer, M., Shinn, M.W., Anticevic, A., Murray, J.D. Generative modeling of brain maps with spatial autocorrelation. Neuroimage, 220 (2020).