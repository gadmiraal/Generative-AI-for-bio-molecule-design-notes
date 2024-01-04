# Scenario 1
Explore the use of a GPT-like model in a language modelling setting with a combination of the all-atom representation & 3Di structure representation. Compare these results with the original all-atom paper[^1] and other similar works 
***
There are two ways you can include the additional 3Di representation on top of the all-atom representation:
- Apply a **co-design** method and include the full atom sequence with the 3Di sequence in the input and output. Each protein 
- Apply a **conditional** method and only include the full atom sequence for the input and output. The 3Di sequence would be used as additional information through the use of attention heads.
# Scenario 2
Cast all-atom representation in a diffusion setting and explore different setups
***

# Scenario 3
Explore different model architectures to find which works best with long sequence lengths (i.e. mamba, hyena, etc.)
***
Transformer were initially the SOTA for handling sequences of longer lengths. One of there major downsides is that transformers scale quadratic with sequence length because of the attention mechanism which is undesirable for significantly long sequence lengths. Recently different models  like Hyena and MAMBA were developed which can handle even longer sequence and also scale linearly with length.

Proteins modelling has thus far only been done with primarily smaller amino acid sequence length (max several hundreds) because of space and time limitations. These newer models could pave the way to explore the possibility to better model and design proteins of longer lengths. This also opens up to the way to better explore the all-atom protein representation for proteins. This representation blows up the the already long amino acids representation to even greater lengths. 
# Scenario 4
Explore different combinations of protein sequence and structure representations
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