## Discrete Diffusion
[[Diffusion Model|Diffusion models]] are normally in set in a continuous setting where the original distribution with real values are transformed to a simple continuous distribution such as a Gaussian distribution. This raises some issues when we are trying to generate text with a fixed alphabet. To combat this, several solution can be used which all fall under discrete diffusion. 



## Generation
We start with pure noise $x_T$ (that is a uniform random sequence of our vocabulary)
Then for $T \rightarrow 1$  we do
	predict the logits $\hat{x}_0$ from $x_t$ and $t$ using our trained neural network
	get the posterior from the predicted logits $q(\hat{x}_0 | x_t)$
	on this posterior we add some noise if it is not the first step
	we take the argmax on the first dimension


Get 
Get predicted posterior logits $q(x_0|x_t, t)$ 