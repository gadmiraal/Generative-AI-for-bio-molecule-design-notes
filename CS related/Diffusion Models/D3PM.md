## Discrete Diffusion
[[Diffusion Model|Diffusion models]] are normally in set in a continuous setting where the original distribution with real values are transformed to a simple continuous distribution such as a Gaussian distribution. This raises some issues when we are trying to generate text with a fixed alphabet. To combat this, several solution can be used which all fall under discrete diffusion. 



## Generation
Get logits $\hat{x}_0$ from $x_t$ and $t$ 
Get predicted posterior logits $q(x_0|x_t, t)$ 