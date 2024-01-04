Use GPT with a combination of the all-atom & 3Di representation and compare with original all-atom paper [[D. Flam-Sheperd et al. (2023) - Atom-by-atom protein generatio and beyond with language models.pdf]]
***
There are two ways you can include the additional 3Di representation on top of the all-atom representation:
- Apply a **co-design** method and include the full atom sequence with the 3Di sequence in the input and output. Each protein 
- Apply a **conditional** method and only include the full atom sequence for the input and output. The 3Di sequence would be used as additional information through the use of attention heads.