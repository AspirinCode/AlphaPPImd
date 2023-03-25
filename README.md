# TransPPImd
**Exploring the conformational space of protein-protein complexes with transformer-based generative neural networks**
Protein-protein interactions are the basis of many protein functions, and understanding the contact and conformational changes of protein-protein interactions is crucial for linking protein structure to biological function. Although difficult to detect experimentally, molecular dynamics (MD) simulations are widely used to study the conformational space and dynamics of protein-protein complexes, but there are significant limitations in sampling efficiency and computational costs. In this study, a generative neural network was trained on protein-protein complex conformations obtained from molecular simulations to directly generate new conformations with physical realism. We demonstrated the use of a deep learning model based on the transformer architecture to explore the conformational space of protein-protein complexes through MD simulations. The results showed that the learned latent space can be used to generate unsampled conformations of protein-protein complexes for obtaining new conformations complementing pre-existing ones, which can be used as an exploratory tool for the analysis and enhancement of molecular simulations of protein-protein complexes.


## Acknowledgements
We thank the authors of C5T5: Controllable Generation of Organic Molecules with Transformers and IUPAC2Struct: Transformer-based artificial neural networks for the conversion between chemical notations for releasing their code. The code in this repository is based on their source code release (https://github.com/dhroth/c5t5 and https://github.com/sergsb/IUPAC2Struct). If you find this code useful, please consider citing their work.


## Requirements
```python
Python==3.7
biopython==1.7.9
openmm==7.7.0
mdanalysis==2.1.0
mdtraj==1.9.7
pytraj==2.0.6
modeller==10.2
nglview==3.0.3
tensorflow==2.8.0
```




## Molecular dynamics


```python

```

## Model Metrics




## License
Code is released under MIT LICENSE.


## Cite:



