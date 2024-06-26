[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](https://github.com/AspirinCode/DeepPPImd)
[![bioRxiv](https://img.shields.io/badge/bioRxiv2024.02.24.581708-green)](https://doi.org/10.1101/2024.02.24.581708)
[![bioRxiv](https://img.shields.io/badge/10.1021%2Facs.jctc.4c00255-pink)](https://doi.org/10.1021/acs.jctc.4c00255)


# AlphaPPImd
**Exploring the conformational ensembles of protein-protein complexes with transformer-based generative model**  

Protein-protein interactions are the basis of many protein functions, and understanding the contact and conformational changes of protein-protein interactions is crucial for linking protein structure to biological function. Although difficult to detect experimentally, molecular dynamics (MD) simulations are widely used to study the conformational space and dynamics of protein-protein complexes, but there are significant limitations in sampling efficiency and computational costs. In this study, a generative neural network was trained on protein-protein complex conformations obtained from molecular simulations to directly generate new conformations with physical realism. We demonstrated the use of a deep learning model based on the transformer architecture to explore the conformational space of protein-protein complexes through MD simulations. The results showed that the learned latent space can be used to generate unsampled conformations of protein-protein complexes for obtaining new conformations complementing pre-existing ones, which can be used as an exploratory tool for the analysis and enhancement of molecular simulations of protein-protein complexes.


## Framework of AlphaPPImd
![Model Architecture of AlphaPPImd](https://github.com/AspirinCode/AlphaPPImd/blob/main/figure/DeepPPImd_framework.png)


## Acknowledgements
We thank the authors of Molecular dynamics without molecules: searching the conformational space of proteins with generative neural networks for releasing their code. The code in this repository is based on their source code release (https://github.com/dgattiwsu/MD_without_molecules). If you find this code useful, please consider citing their work.


## News!

**[2024/05/30]** AlphaPPImd is [online(J. Chem. Theory Comput.)](https://doi.org/10.1021/acs.jctc.4c00255).

**[2024/05/22]** Accepted in **Journal of Chemical Theory and Computation**, 2024.



## Requirements
```python
Python==3.7
biopython==1.7.9
ambertools==21    #conda install -c conda-forge ambertools=23
openmm==7.7.0
mdanalysis==2.1.0
mdtraj==1.9.7
pytraj==2.0.6
modeller==10.2
nglview==3.0.3
tensorflow==2.8.0
```


*  biopython

https://github.com/biopython/biopython

*  OpenMM

https://openmm.org/

*  modeller

https://salilab.org/modeller/

*  MDAnalysis

https://www.mdanalysis.org/

*  nglview

https://github.com/nglviewer/nglview

*  pytraj

https://github.com/Amber-MD/pytraj

*  mdtraj

https://github.com/mdtraj/mdtraj


## Molecular dynamics

### prpepare  topology and coordinate files
```python
pdb4amber -i A.pdb -o a.pdb -y -d

pdb4amber -i a.pdb -o inputA.pdb --reduce

pdb4amber -i B.pdb -o b.pdb -y -d

pdb4amber -i b.pdb -o inputB.pdb --reduce


************tleap.in**********************************************
source leaprc.protein.ff14SB #Source leaprc file for ff14SB protein force field
source leaprc.water.tip3p #Source leaprc file for TIP3P water model

ProA = loadpdb inputA.pdb #Load A PDB file for protein
ProB = loadpdb inputB.pdb #Load B PDB file for protein

mol = combine {ProA,ProB}

check mol
solvatebox mol TIP3PBOX 12.0 #Solvate the complex with a cubic water box
addions mol Cl- 0 #Add Cl- ions to neutralize the system
addions mol Na+ 0 #Add Na+ ions to neutralize the system
charge mol
savepdb mol ppcomplex_solv.pdb
saveamberparm mol ppcomplex_solv.prmtop ppcomplex_solv.inpcrd #Save AMBER topology and coordinate files
quit #Quit tleap program
**********************************************************************

tleap -s -f tleap.in > tleap.out

```

### run rolecular dynamics

```python

python run_openmm_simulation.py

```


## Model Metrics

### DockQ
DockQ: A Quality Measure for Protein-Protein Docking Models

https://github.com/bjornwallner/DockQ

*  Basu, S. and Wallner, B., 2016. DockQ: a quality measure for protein-protein docking models. PloS one, 11(8), p.e0161879.
*  Mirabello, C. and Wallner, B., 2024. DockQ v2: Improved automatic quality measure for protein multimers, nucleic acids, and small molecules. bioRxiv, pp.2024-05.  

## License
Code is released under MIT LICENSE.


## Cite:
*  Jianmin Wang, Xun Wang, Yanyi Chu, Chunyan Li, Xue Li, Xiangyu Meng, Yitian Fang, Kyoung Tai No, Jiashun Mao, Xiangxiang Zeng. **"Exploring the conformational ensembles of protein-protein complex with transformer-based generative model."** Journal of Chemical Theory and Computation; doi: https://doi.org/10.1021/acs.jctc.4c00255
*  Schwing, Gregory, Luigi L. Palese, Ariel Fernández, Loren Schwiebert, and Domenico L. Gatti. **"Molecular dynamics without molecules: searching the conformational space of proteins with generative neural networks."** arXiv preprint arXiv:2206.04683 (2022).
*  Jianmin Wang, Xun Wang, Yanyi Chu, Chunyan Li, Xue Li, Xiangyu Meng, Yitian Fang, Kyoung Tai No, Jiashun Mao, Xiangxiang Zeng. **"Exploring the conformational ensembles of protein-protein complex with transformer-based generative model."** bioRxiv 2024.02.24.581708; doi: https://doi.org/10.1101/2024.02.24.581708
