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
### More fleshed out ideas
#### Idea 1
Use ProtGPT2 and fine tune it on the all atom representation in combination with 3Di. Then use it to do sequence and structure prediction
#### Idea 2
Train the all atom representation on a GPT like architecture and finetune for sequence and structure prediction
#### Idea 3
Use an atom-by-atom pLM to obtain certain feature embeddings for a diffusion task
#### Idea 4
We use the all atom representation + the 3Di tokens for a rich representation of a protein both in 1D and in 3D space. We create the model in such a way that 3Di tokens are optional so we can do an ablation study on the effects of using both. Furthermore we can even use MSA for an even richer representation, which we should also ablate. Due to computational power it might be better to for now only try this on smaller proteins of a length of max 500(?) amino acids. We can then use three types of language models
- **Bert**: Use an encoder architecture to map protein to an embedding/latent space which can then be used for feature extraction like secondary structure prediction, contact prediction, remote homology detection and etc.
- **GPT**: Use an decoder architecture 