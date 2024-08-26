## Introduction
ByteNet  is a a 1D convolutional approach for [[Seq2Seq]] language modelling. It uses dilation to increase its context window and allows for linearly scaling with sequence length. [[Transformer||Transformers]] which are traditionally used for Seq2Seq have a context window which scales quadratic.

[*"For sequences, the EvoDiff denoising model adopts a ByteNet-style CNN architecture previously shown to perform similarly to transformers for protein sequence masked language modeling tasks"*](https://www.biorxiv.org/content/10.1101/2023.09.11.556673v1.abstract)

## Method
The proposed ByteNet architecture is composed of a decoder that is stacked on an encoder and generates variable-length outputs via dynamic unfolding. The decoder is a language model that is formed of one-dimensional convolutional layers that are masked and use dilation. The encoder processes the source string into a representation and is formed of one-dimensional convolutional layers that use dilation but are not masked.

