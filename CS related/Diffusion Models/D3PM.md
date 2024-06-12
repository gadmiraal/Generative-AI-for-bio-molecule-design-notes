## Discrete Diffusion
[[Diffusion Model|Diffusion models]] are normally in set in a continuous setting where the original distribution with real values are transformed to a simple continuous distribution such as a Gaussian distribution. This raises some issues when we are trying to generate text with a fixed alphabet. To combat this, several solution can be used which all fall under discrete diffusion. 



## Generation
We start with pure noise $x_T$ (that is a uniform random sequence of our vocabulary)
Then for $T \rightarrow 1$  we do
	Predict the logits $\hat{x}_0$ from $x_t$ and $t$ using our trained neural network
	Get the posterior from the predicted logits $q(\hat{x}_0 | x_t)$
	Create Gumbel noise $\epsilon$  
	On this posterior we add some noise if it is not the first step
	We set $x_{t-1} by taking the argmax on the first dimension (we are using one-hot so we see which token in our vocabulary is most likely)
Return $x_0$

Gumbel noise is added to the logits of the categorical distribution to introduce randomness, allowing for stochastic sampling. This approach is crucial for tasks where sampling needs to reflect the probabilities of the categories, rather than deterministically picking the highest probability every time