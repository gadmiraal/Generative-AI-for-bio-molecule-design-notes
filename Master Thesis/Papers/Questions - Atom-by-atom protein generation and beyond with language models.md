1. Why use [[Atom-by-atom#SELFIES]] instead of [[Atom-by-atom#SMILES]]? What is the difference and advantageous/disadvantageous? 
2. Data augmentation is done by randomizing the atom orderings of each protein using `rdkit`, why is this a valid augmentation? Since one cannot guarantee that this reordering creates a valid protein?
3. When creating the model for non-standard amino acids, did you think about pre-training on standard amino acids and then fine-tune the model on non-standard amino acids sequences? 
4. Did you test against other models?
5. What are the prospects of generating synthetic amino acids?
6. You state that most frequency distributions are similar but some seem to be shifted/skewed towards the left
	![[Pasted image 20231122142000.png]] 
1. How is similarity with training set proteins measured?
	1. FASTA
2. Why do you train/generate on smaller size proteins for the unnatural amino acid model?
3. How are these unnatural amino acids constructed exactly/precisely?
	1. Randomly attaching fragments is effective why? Can't we do this more decisive (targeted more precisely)?
4. Include some form of conditioning?
5. How do they know that the conjugates are stable?
6. How can a vocabulary be around 30 tokens, is it not supposed to be a precise number