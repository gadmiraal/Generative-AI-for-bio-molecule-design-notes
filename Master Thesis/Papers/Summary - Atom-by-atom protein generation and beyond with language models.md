Original paper: [[D. Flam-Sheperd et al. (2023) - Atom-by-atom protein generatio and beyond with language models.pdf]]
***
[[Language Models for protein design]] (CLMs) have seen great success in generating large and complex molecules by using [[Atom-by-atom]] representation[^1] . By using these CLMs the authors show that these models can also create sequences for [[Proteins]] . They verified the validity of their new sequences by using [[AlphaFold]] to predict structure given sequence. Additionally they found that their model is able to generate novel amino acid sidechains which are more complex than the standard [[Amino acids]]. Lastly, they showed that their CLM can also generate novel proteins and small molecules together as protein drug conjugates
## Method

### Dataset
In this study, the datasets are constructed by using small proteins from the [[Protein Data Bank]] (PDB), specifically between 50 and 150 residues. After applying some viability constraints on the PDB they decrease the total amount of effective proteins. Then they use data augmentation to increase the amount of training data. This augmentation is done by randomizing the atom orderings of each protein in `rdkit` to obtain multiple copies of each biomolecule. <span style="color:#ff0000">But it does not state why this is an effective way to do this.</span> The resulting datasets are of the size of around ~$250K$ sequences.
### Chemical Language Model
The vocabulary $\mathcal{T}$ consists out of chemical tokens that are defined using the standard SELFIES tokens. This vocabulary is or <span style="color:#ff0000">around 30 tokens</span>. A macromolecule is composed of variable length sequences of tokens from a chemical language $[\text{CT}]_1$ where $\text{CT} \in \mathcal{T}$ such that $$\text{MOL} = ([\text{CT}]_1,[\text{CT}]_2, \ldots, [\text{CT}]_n)$$The model tries to predict the joint probabilities using a [[Language models#Transformer]] over a single molecule as such $$p(\text{MOL}) = \prod_{i=n}^{n} p([\text{CT}]_n | [\text{CT}]_{n-1}, \ldots, [\text{CT}]_1)$$The precise architecture they use is a GPT-like architecture with 4 attention heads and between 1 and 10 million parameters.
## Results
### Novel protein generation
During the experiment they generate a thousand samples and evaluate their atom, residue, and protein-level properties. 
First, they analyse the backbone structure and check if the generated sidechains are amino acid residues. They conclude that around $70\%$ of the generated samples are in fact proteins and all these protein samples are unique and novel. 
Next they compare the distribution of amino acids for the generated samples and the training examples. For the most part do these distributions overlap but there are some outliers. As well as that for the most part the distributions seems to be shifted/skewed to the left (lower frequencies).
Thirdly, they check if their generated proteins are structurally sound using AlphaFold. They find that their generated proteins have a confidence between 70-90 pLDDT. This is a confidence score based per-residue Laplace-Filtered Distance-Deviation Z-score where the values range from 0 to 100. As a baseline, random protein sequence have a score below 50 pLDDT. From the AlphaFold result can they conclude that these proteins have also valid secondary and tertiary structures 
Lastly, they state that their samples are between $86\% - 40\%$ similar to the proteins in the training data showcasing that the model takes inspiration from the training set but does not memorize them. <span style="color:#ff0000">It is not mentioned how this similarity is calculated</span>.
### Proteins with unnatural amino acids
The authors tried testing a novel idea with their CLM, they wanted to create novel unnatural amino acid sidechains for proteins. To create their dataset they modify each sidechain on each protein by attaching a random fragment to a random attachment point. After training they again generate a thousand samples.
From their results they show that the CLM can learn the correct distribution of carbon, hydrogen and oxygen atoms compared to the training set as well as learning the atom-level properties octanol-water partition coefficient (LogP), exact molecular weight (MW) and the topological polar and surface area (PSA).
Furthermore, it also learns the a similar distribution of chemical fragments compared to the training set.
Finally, it does seem that the model generates shorter backbones and fewer atoms than the proteins in the training set.
### Antibody drug conjugate
Lastly do the authors test if CLM can correctly model antibody-drug conjugates, which are a form of cancer therapy intended to target and kill cancer cells but spare healthy cells. Structurally, they are composed of an antibody attached to single or multiple anticancer drugs typically using some linker molecule. To create their dataset they attach a single drug-like molecule to single-domain antibodies. Where they use two possible linkers for the amino acids cysteine and lysine each. After training they again generate a thousand samples
First they again check if the generated samples are indeed proteins and fold into confident structures, which they do. 
Then they strip the "warheads" from the conjugates. Warheads in their context include the sidechain, linker and the small molecule. From this they can see that the attached molecules different and are structurally similar to those in the training warheads
They also compare several properties of the generated warheads with the training warheads. For the most part are these properties similar except that the model slightly underestimates QED and SA properties as well as the number of ring atoms present.
Finally they find that the generated warheads are novel and unique.
## Discussion




## Questions
[[Questions - Atom-by-atom protein generation and beyond with language models]]


[^1]: [[D. Flam-Shepherd et al. (2022) - Language models can learn complex molecular.pdf]]