## Template - Paper title
- What does it do? Predict/Generate
- How is protein defined
- How is noising done
- What is the architecture
- <span style="color:#ff0000">More?</span>
## Final Table
[Excel table](file:///C:\Obsidian%20Vault\Generative%20AI%20for%20(bio)molecule%20design\Literature%20Survey\Papers/paper_table.xlsx)
## Papers
- [[Anand, Namrata, et al. Protein Structure and Sequence Generation with Equivariant Denoising Diffusion Probabilistic Models.pdf]]
	- Generates a protein sequence and structure
	- Define protein for each residue: 3D coordinates of alpha carbon, the global rotation around the alpha carbon (used to infer rest of residue backbone), the amino acid type of residue and the 4 angles to find sidechain position
	- Use discrete masked denoising. They mask a proportion of the protein during training and learn to unmask. During sampling they start with a fully masked protein and "find" a new one by unmasking
	- The architecture is an equivariant transformer

-  [[Wu, Kevin E., et al. Protein structure generation via folding diffusion.pdf]]
	- Predicts structure from sequence
	- Define protein by vector of 6 angles that describe the relative position of backbone atoms in next residue given current residue
	- Use a wrapped normal distribution and a wrap function to handle periodicity of angular values
	- The architecture is a vanilla bidirectional transformer with relative positional embeddings