an analysis of read papers can be found here: [[Paper Notes on Diffusion for Protein Prediction]]
a list of interesting papers can be found here: [[Interesting Papers Literature Survey]]
***
## Terminology
- **In vivo** investigations involve human or animal studies
- **In vitro** experiments study digestion outside the body
- **In silico** models simulate digestive processes using numerical and computational methods
- **Ab initio** deign means designing from the beginning or the ground up
## What are proteins
[[Proteins]] are large bio molecules that are comprised out of amino acids that form unique complex folded structures. Proteins play an important role in a significant amount of bio process in living organisms. Their function can range from catalysing metabolic reactions, aiding the immune system, transporting molecules and many more. 
## Designing proteins
Due to their importance in many biological processes it can be extremely beneficial to design novel proteins. These designed proteins can aid in many tasks such as helping cure diseases as Alzheimer and cancer but also <span style="color:#ff0000">what else?</span>
The difficulty of designing proteins stems from the complexity of proteins <span style="color:#ff0000">add more here</span> 
## Prediction Models
[[Diffusion Model]]
[[Guidance in Diffusion Models]]
[[Equivariant Neural Network Models]]
[[Wrapped Normal Diffusion Process]]
## Structure-to-Sequence Prediction
**Structure-to-Sequence prediction** or **inverse folding** tries to map a generated structure back to its supposed amino acid sequence. The reason for going from structure to sequence is because of the biological principle that protein function is determined by structure and structure is determined by sequence. Hence if one wants to design a protein for its function it seems logical to first generate the structure and from this derive the final sequence. 
<span style="color:#ff0000">One problem with this approach is that multiple sequences can be derived from one structure or that the sequence may not be found even though it exists</span>
## Sequence-to-Structure Prediction
Sequence-to-Structure prediction tries to map a given or generated structure to its high-level structure. Since a protein has a dynamic structure, it is smart to use a generative distribution model like a diffusion model . <span style="color:#ff0000">To be continued</span>
One advantage of this process is that the availability of data for protein sequence is far greater than the availability of qualitative protein structural data thus making training more efficient and thorough. Furthermore, protein sequence models are quicker in giving predictions than protein structure prediction.
## Generative protein modelling

## Post Processing
Post-processing: Alternating Direction Method of Multipliers (ADMM) and Rosetta

## Data
Most data is contained in the [[Protein Data Bank]]

## Assessment

### Structure assessment
- pLLDT, AlphaFold gives a confidence of domains in a structure. From their video: https://www.youtube.com/watch?v=tTN0MM2CQLU, they say that below 50 is a structure domain that is not to be trusted. They also might say that this domain is inherently disordered in nature. Also pLLDT is only for single domains and not interdomain confidence (so all high domains does not mean a high confidence in the total structure)
- Predicted Aligned Error (PAE), how confident it is in the placement of domains relatively to each other