## SMILES
Simplified Molecular-Input Line-Entry System (SMILES) was created in 1988 with the goal to aid "modern chemical information processing". It was developed with a focus on molecular graph theory, which allowed it to obtain a grammar that is both minimal and natural. Over the years SMILES has become ubiquitous in the field of cheminformatics to represent molecules. 


![smiles](https://upload.wikimedia.org/wikipedia/commons/0/00/SMILES.png)

An example of the SMILES representation is shown in the figure above. In SMILES, molecules are defined as a chain of atoms, which are written as letters in a string. Branches in the molecule are defined within parentheses, while ring closures are indicated by two matching numbers. The SMILES grammar, though simple, allows for the description of complex structures as well as properties such as stereochemistry, aromatic bonds, chirality, ions, and isotopes.

Even though its ubiquity SMILES still suffers from some flaws. The first being that for a single molecule several string representations are possible. This can be fixed by getting the canonical string from [[RDKit]]. The second is that one can create many SMILES strings that do not map to a valid molecule. This is especially problematic for the generation of novel molecules.

## SELFIES
SELF-referencing embedded string (SELFIES) is a 100% robust molecular string representation, meaning that all 