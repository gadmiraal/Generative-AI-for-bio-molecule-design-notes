# Scenario 1
*Explore the use of a GPT-like model in a language modelling setting with a combination of the all-atom representation & 3Di structure representation. Compare these results with the original all-atom paper[^1] and other similar works* 
***
There are two ways you can include the additional 3Di representation on top of the all-atom representation:
- Apply a **co-design** method and include the full atom sequence with the 3Di sequence in the input and output. The model learns the connection between sequence and structure of a protein allowing to design better proteins. 
- Apply a **conditional** method and only include the full atom sequence for the input and output. The 3Di sequence would be used as additional information through the use of attention heads.
# Scenario 2
*Explore how the all-atom representation can be used in a diffusion setting and explore different diffusion setups*
***
Different experiments where we fix all but one variable and explore the results.

Different experimental variables
**Architecture**
- Transformer
- MLP
- UNET
- (Optional) newer models like Hyena and MAMBA
**Discrete diffusion types**
- Apply categorical noise directly to sequence (use a masking technique)
- Apply Gaussian noise to token-vector embeddings
**Sequence representations**
- All-atom representation using SMILES or SELFIES
	- Maybe use the representation which has on average a shorter length?
	- Original paper[^1] uses SELFIES
- Functional groups or atom motifs (e.g. $-OH$, $-NH_2$ or $-CH_3$ ) 
- Amino acids
- Amino acids motifs (e.g. $\alpha$-Helices or $\beta$-plate )
**Include additional information**
- 3Di tokens
	- An encoded sequence that describes the structure of a protein per amino acid
- Protein Language Model (PML) features
	- PMLs are trained to extract meaningful features from a proteins sequence 
- Multiple Sequence Alignment (MSA)
	- Since proteins can be similar due to evolution we can use (structural) information from proteins whose sequences align
**Augmentation on all atom representation**
- No augmentation so we use only SMILES canonical ordering
- Unrestricted randomized SMILES ordering
- Restricted randomized SMILES ordering **restricted has already been found to be the best[^2]**
**Objectives**
- De novo generation
	- Generate completely new proteins which have not been found in nature (yet)
- Inpainting
	- Remove a part of the protein and generate a new replacement part 
- Guided or non-guided
	- A diffusion model can be guided to a certain sub-distribution during sampling. This can  be done using the following methods: Classifier, Gradient or Gradient-Free 
- Finetune on unnatural amino acids
	- After the all-atom model is created and trained we can fine-tune the model further on unnatural amino acids
**What to compare**
- Training time
- Loss on training, validation and test set
- Protein validity
	- Are generated molecules in fact proteins
- Atom distribution
	- How well do we capture the training atom distribution with the generated proteins
- Structural validity
	- Check if the generated proteins are structurally valid using AF2
- Diversity
	- How diverse or similar are the generated proteins compared to the training data 
**Datasets**
- Protein Data Bank (PDB)
- …

### Research question
### Experiments
**Which architecture to use for all atom representation**
Train different diffusion models with different architectures and see which is the best. We can compare on training time and loss 

**Which type of discrete diffusion to try**
Train two models where we compare categorical noise and gaussian noise

**Comparison of representation**
Train two models were we compare all-atom sequence vs. AA sequence

**Testing multiple subsets of protein length**
Train multiple models were we compare how well the architecture can handle different protein lengths. Note that each model should have the same amount of training data for a fair comparison. We can compare on protein validity, atom distribution, structural validity and diversity

**To augment or not to augment?**
Train two models where one is trained with data augmentation using restricted randomized SMILES ordering and the other is not. We compare on protein validity, atom distribution, structural validity and diversity. 


# Scenario 3
*Explore different model architectures to find which works best with long sequence lengths (i.e. mamba, hyena, etc.)*
***
Transformer were initially the SOTA for handling sequences of longer lengths. One of there major downsides is that transformers scale quadratic with sequence length because of the attention mechanism which is undesirable for significantly long sequence lengths. Recently different models  like Hyena and MAMBA were developed which can handle even longer sequence and also scale linearly with length.

Proteins modelling has thus far only been done with primarily smaller amino acid sequence length (max several hundreds) because of space and time limitations. These newer models could pave the way to explore the possibility to better model and design proteins of longer lengths. This also opens up to the way to better explore the all-atom protein representation for proteins. This representation blows up the the already long amino acids representation to even greater lengths. 
# Scenario 4
*Explore different combinations of protein sequence and structure representations and find optimal settings*
***
There exists several possibilities to represent a protein both structurally and sequentially. These representation are given below and are ordered from the most low-level, information rich and flexible option to the most high-level, information poor and more strict option.

**Sequence representations**
- All-atom representation
- Functional groups (atom motifs)
- Amino acids
- Amino acids motifs
**Structure representations**
- Atom-specific coordinates
- $C_\alpha$ placements with the 6 rotational angles
- Only $C_\alpha$ placement



[^1]: [[D. Flam-Sheperd et al. (2023) - Atom-by-atom protein generatio and beyond with language models.pdf]]
[^2]: [[J. Arus-Pous, et al (2019) - Randomized SMILES strings improve the quality of molecular generative models.pdf]]