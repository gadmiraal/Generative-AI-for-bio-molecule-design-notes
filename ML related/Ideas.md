Many models can only be as good as its data, how can these new models surpass its training data?
	Look at AlphaGo 
	How can it generate sequences from unexplored regions

InstructGPT

Atom-by-atom might be useful for mutations?

There is no good tokenization yet for proteins so maybe a reason to do atom-by-atom from [[B. Hu et al. (2022) - Protein Language Models and Structure Prediction Connection and Progression.pdf]]:
	Compared with algorithms in NLP, protein tokenization methods still remain at a low level without a well-defined and biologically meaningful protein token algorithm (Vu et al., 2022). This may be a direction for unlocking the secrets of proteins.
## Idea 1
Use a pretrained GPT like architecture and fine tune it on the all atom representation and use it to do sequence and structure prediction
## Idea 2
Train the all atom representation on a GPT like architecture and finetune for sequence and structure prediction
## Idea 3
Use an atom-by-atom pLM to obtain certain feature embeddings for a diffusion task
