[[Language models]], specifically [[Language models#Transformer]]-like architectures, have become a staple in the field of [[Protein Design]]. Several works use these language models to create novel sequences of [[Proteins]] using token generation architectures like [[Language models#GPT]]. Other models started using these language capabilities to extract protein feature information from a given sequence of [[Amino acids]] using [[Language models#BERT]]-like architecture.
***
## Encoder-based protein language models  
Several encoder-based models have emerged in recent years to encode protein sequences into embeddings, facilitating downstream tasks like secondary structure prediction, contact prediction, remote homology detection, and fluorescent landscape and stability landscape prediction.  

1. **TAPE (Task Assessing Protein Embeddings)[^1]:** An early language model utilizing an encoder-only transformer architecture to obtain embedded representations of proteins. These embeddings were then utilized in various supervised models for tasks such as secondary structure and contact prediction, remote homology detection, and landscape predictions.  
2. **ESM (Evolutionary Scale Modelling)[^2]:** A BERT-based model with 33 layers, trained on 250M protein sequences. ESM encodes properties of proteins at different hierarchical levels, achieving state-of-the-art predictions on long-range contacts and mutational effects. It has also demonstrated efficacy in evolving human antibodies with improved binding affinity and activity against Ebola and SARS-CoV2 viruses[^3].  
3. **ProteinBERT[^4]:** This model modifies the original BERT Encoder-Transformer to obtain "functionally aware" protein representations. It simultaneously learns local protein sequences and their GO annotations in separate encoder modules. These modules are trained in parallel, influencing each other through a global Attention module. The pre-trained model is fine-tuned for various downstream tasks, including secondary structure prediction, remote homology, fold classes, signal peptide predictions, and post-translation and biophysical properties prediction. 
4. **ReLSO (Regularized Latent Space Optimization):**[^5] Another model that significantly modifies the BERT Transformer. ReLSO's Encoder blocks incorporate innovative dimensionality reduction techniques based on the Attention mechanism, deep convolutional layers, and dense FFNN. This approach effectively models the sequence-function protein landscape and generates high-fitness sequences[^5].   
5. **ProtTrans**[^13]
6. **GearNet**[^14]
7. **Steps**[^15]
8. **SaProt**[^12] which uses a combination of 3Di tokens and amino acids tokens to create a sequence which entails both sequence and structure properties. The SaProt model surpasses well-established and renowned baselines across 10 significant downstream tasks, demonstrating its exceptional capacity and broad applicability.

[^1]: Rao et al., 2019
[^2]: Rives et al., 2021 
[^3]: Hie et al., 2023
[^4]: Brandes et al., 2022
[^5]: Castro et al., 2022
[^13]:  Elnaggar et al. 2021
[^14]:  Zhang et al. 2022
[^15]:  Chen et al. 2022

## Decoder-based generative protein language models
Using only the decoder part of an transformer gives us the ability to generate and finish sequences. This is done using a GPT-like architecture and masked self-attention layers.

1. **ProtGPT2**[^6] is a based on the GPT-2 architecture that is able to generate proteins. It is trained on 50 million proteins drawn from the Uniref50 clustered sets of UniProtKB sequences. While it can generate de novo protein sequences similar to natural ones it can also explore protein regions unexplored by natural evolution. The new sequences, despite their relative sequence diversity compared to naturally occurring proteins, show structural similarity, predicted stability and several common properties with proteins sampled by natural selection
2. **Design in Areas of Restricted Knowledge (DARK)[^7]** used a novel decoder architecture for protein design. Additionally it is trained on synthetic sequences which still resulted in that the model could generate novel stable and ordered structures (as verified by [[AlphaFold]]-2)
3. A recent work used a GPT architecture in conjunction with an [[Atom-by-atom]] representation of the protein sequence. The results thus far show that the model can indeed create foldable amino acid sequences and can correctly replicate the distribution of the training set. How it performs against other similar models still has to be tested. 

[^6]: Ferruz and Hocker, 2022
[^7]: Moffat et al., 2022

## Conditional transformers for the design of functionally characterized proteins

TBD
## Encoder-Decoder protein language translation
Transformers were originally created to do natural language machine translation. Following this principle researches used the translation capabilities of the full transformers in the field of protein design. One approach is to translate proteins into its binding ligand and vice versa. Another approach is to translate 1D amino acids sequence into 1D structure sequences using 3Di tokens (from FoldSeek[^11]).

1. The original Encoder-Decoder Transformer architecture was used to translate a protein into its corresponding ligand using the [[Atom-by-atom#SMILES]] format[^8]. The encoder is used to generate a protein embedding while the decoder translates this embedding into a corresponding binding target. This novel approach opened up the way to in silico de novo engineering of protein drugs that bind to specific molecular targets,
2. Another approach[^9] used the Transformer architecture to generate enzymes that catalyse the chemical reactions of specific reactants.
3. **ProstT5**[^10] uses Transformers in combination with 3Di tokens to be able to "fold" a proteins amino acid sequence to a 3Di sequence of tokens specifying the proteins structure and also perform inverse folding by using the transformer in the reverse way. They used a non-redundant dataset from the AlphaFoldDB and fine-tuned an existing pLM(ProtT5). It excels at remote homology detection and protein design.
4. 

[^8]: Grechishnikova (2021)
[^9]: Schwaller et al. (2021)
[^10]: Heinzinger et al. (2023)
[^11]: https://search.foldseek.com
[^12]: Anonymous authors - Under review as a conference paper at ICLR 2024 - SAPROT: PROTEIN LANGUAGE MODELING WITH STRUCTURE-AWARE VOCABULARY

