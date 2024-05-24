## SMILES
Simplified Molecular-Input Line-Entry System (SMILES) was created in 1988 with the goal to aid "modern chemical information processing". It was developed with a focus on molecular graph theory, which allowed it to obtain a grammar that is both minimal and natural. Over the years SMILES has become ubiquitous in the field of cheminformatics to represent molecules. 


![smiles](https://upload.wikimedia.org/wikipedia/commons/0/00/SMILES.png)

An example of the SMILES representation is shown in the figure above. In SMILES, molecules are defined as a chain of atoms, which are written as letters in a string. Branches in the molecule are defined within parentheses, while ring closures are indicated by two matching numbers. The SMILES grammar, though simple, allows for the description of complex structures as well as properties such as stereochemistry, aromatic bonds, chirality, ions, and isotopes.

Even though its ubiquity SMILES still suffers from some flaws. The first being that for a single molecule several string representations are possible. This can be fixed by getting the canonical string from [[RDKit]]. The second is that one can create many SMILES strings that do not map to a valid molecule. For example a string could be missing a open or close parantheses for a ring ("CC(CCCC"). Another example is that a string might violate chemical properties such as a triple bond on an oxygen atom ("C0=CC"). This issue is especially problematic for the generation of novel molecules using generative models.

## SELFIES
SELF-referencing embedded string (SELFIES) is a 100% robust molecular string representation, meaning that any possible combination of tokens correspond to a chemically valid molecule. SELFIES is a formal grammar (or automaton) with derivation rules. This can be understood as a small computer program with minimal memory to achieve 100% robust derivation. The SELFIES grammar is designed with the explicit aim of eliminating syntactically and semantically invalid molecules, for example in generative tasks.

### Overloading
Overloading refers to the practice of assigning multiple meanings or functions to a single symbol or operator, depending on the context in which it is used. This concept is often encountered in programming languages where a single function name can perform different tasks based on the type or number of its arguments. An example how overloading is used in programming languages can be seen below

```
int add(int a, int b) { return a + b; }
float add(float a, float b) { return a + b; }
```

In SELFIES overloading is also used to encode chemical structures in a way that eliminates syntactic errors, such as unbalanced parentheses or ring identifiers, which is possible in SMILES. 
Special symbols (such as \[Branch1\] or \[Ring1\]) start a branch or ring. Instead of using an end symbol, the subsequent token in the string defines the length of the branch or ring.
