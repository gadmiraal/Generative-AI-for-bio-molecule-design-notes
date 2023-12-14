### Types
#### RNN
Recurrent Neural Networks (RNNs)
#### LSTM
Long Short-term Memory (LSTM)
#### Transformer
A transformer is a deep neural network composed of two main components: an Encoder and a Decoder. They make use of attention mechanisms which help look at all hidden states from the encoder sequence for making predictions. Additionally, each of these components is modular and includes a stack of repeated blocks in which each module is the input of the subsequent one. 

Transformers can be used for text translation, classifying, summarisation or for named entity recognition. 

Some important concepts that a transformer possesses which sets it out from previous models:
1. **Self-supervised learning**, a transformer learns in a supervised way without using explicit labels. This is advantageous if we have a large amount of unlabelled data. 
2. **Multi-task and transfer Learning**, a transformer is able to learn multiple tasks at the same time and it acquired knowledge can be transferred onto other to tasks by fine-tuning the base model
3. **Attention mechanism**, 
4. **Self-Attention**, a mechanism to find the semantic relationships between the words of the input sequence. in order to compute a representation of the sequence itself. Using this we can efficiently compute long-range dependencies between the elements of a sequence.
5. **Multi-head attention**, self-attention is computed multiple times in parallel using multiple heads in order to capture the different syntactic and semantic relationships among the elements of the sequence.
6. **Interpretability**, because of the self-attention can each attention head capture different types of syntactic and semantic relationships between the elements of the sequence
7. **Parallel computation**, a transformer is able to process the data in parallel achieving substantial speed-up in computation. Other models like RNNs process the data sequence one by one.
##### BERT
Just the encoder for feature extractions using embeddings
##### GPT
Just the decoder for generating sequences
### Application
[[Language Models for protein design]]