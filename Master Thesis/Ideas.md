# Research Question #1
- **Can a diffusion model with a transformer architecture do both protein sequence to protein structure generation and protein structure to protein sequence generation** 
	- Use the transformers ability to translate to go from sequence to structure and vice versa
		- Like ProstT5 but cast it as a diffusion problem instead of a language problem
	- Use the all atom representation for sequence representation
	- Use … for structure representation
		- Depending on the structure representation do we achieve equivariance?
- Using this we learn a co-design representation of a protein in the transformer model but we do not explicitly do co-design?
- The drawback of this approach is that we do not fully leverage the possibility to design proteins with unnatural amino acids.

# Research Question #2
- **Can a diffusion model with a GPT-like architecture generate *de novo* proteins using an all-atom representation of a protein?**
	- Like the All-Atom paper but cast the problem as a diffusion problem instead of a language problem

### Gedachtespinsel
- Many models can only be as good as its data, how can these new models surpass its training data?
	- Look at AlphaGo 
	- How can it generate sequences from unexplored regions
- InstructGPT, use a larger and better model to teach the smaller model.
- Atom-by-atom might be useful for mutations or indels?
- There is no good tokenization yet for proteins so maybe a reason to do atom-by-atom from [[B. Hu et al. (2022) - Protein Language Models and Structure Prediction Connection and Progression.pdf]]:
	- Compared with algorithms in NLP, protein tokenization methods still remain at a low level without a well-defined and biologically meaningful protein token algorithm (Vu et al., 2022). This may be a direction for unlocking the secrets of proteins.
- Atom-by-atom is informationally richer than only amino acids
- Atom-by-atom learning might result in a learned physics model?
- Atom-by-atom with a transformer model to generate ligands from sequence
- Protein ensemble is a fairly large unexplored part of research
- Diffusion is good for dynamicity of structures
- Atom-by-atom and 3Di representation of protein and diffuse using a transformer 
	- How do you add noise to the atom-by-atom representation
- Building on existing language/diffusion models could be advantageous 
- Ablation maybe for SELFIES and SMILES?
- Is using 3Di states better then using angles?
- You can randomize atom ordering in SMILES and not change underlying structure
### More fleshed out ideas
#### Idea 1
Use ProtGPT2 and fine tune it on the all atom representation in combination with 3Di. Then use it to do sequence and structure prediction
#### Idea 2
Train the all atom representation on a GPT like architecture and finetune for sequence and structure prediction
#### Idea 3
Use an atom-by-atom pLM to obtain certain feature embeddings for a diffusion task
#### Idea 4
We use the all atom representation + the 3Di tokens for a rich representation of a protein both in 1D and in 3D space. We create the model in such a way that 3Di tokens are optional so we can do an ablation study on the effects of using both. Furthermore we can even use MSA/Foldseek for an even richer representation, which we should also ablate. Due to computational power it might be better to for now only try this on smaller proteins of a length of max 500(?) amino acids. We can then use three types of language models for three different types of tasks.
- **BERT**: Use an encoder architecture to map protein to an embedding/latent space which can then be used for feature extraction like secondary structure prediction, contact prediction, remote homology detection and etc.
- **GPT**: Use an decoder architecture to be able to generate new sequences. 
- **Transformer**: Use the full encoder-decoder transformer architecture to translate a protein to its ligand pair. We can also without using the 3Di tokens as input translate the amino acids 1D sequence to its 3Di tokens.

#### Idea 4
We train a smaller model with the all atom representation and fine tune it using a large scale pLM. Like the instructGPT paper.



