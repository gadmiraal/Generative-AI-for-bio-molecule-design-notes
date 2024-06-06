D3PM has some interesting similarities between exisiting probabilistic and langauge modelling approaches.

## BERT
[[Language models#BERT]] can be seen as a one-step diffusion model where the transistion matrix is a mix of uniform and absorbing state. When we set our D3PM model with a $10\%$ chance of a token being absorbed and a $5\%$ chance of being replaced by a different token we get exactly to the BERT denoising objective $L_{vb} - L_T = -E_{q(x_1|x_0)}[\log{p_\theta(x_0|x_1)}] = L_{BERT}$ where $L_T$ is a constant independent of $\theta$ (assuming a fixed prior)


## Generative Masked Language Models
Generative Masked Language Models are generative models that generate text from a sequence of \[MASK\] tokens. They are usually trained by sampling a sequence x0, masking k tokens according to some schedule, and learning to predict the masked tokens given context. 

This making can be done by randomly masking each token with probability $p=k/T$ or by sampling exactly $k$ tokens. The objective usually looks like this:

$$
\min -\mathbb{E}_{q\left(\boldsymbol{x}_0\right)}\left[\mathbb{E}_{k \in\left[1 \ldots\left|\boldsymbol{x}_0\right|\right]}\left[\frac{1}{k} \mathbb{E}_{\boldsymbol{x}_k \text { with } k \text { masked tokens }}\left[\sum_{i \text { with }\left[\boldsymbol{x}_k\right]_{\imath}=m} \log p_\theta\left(\left[x_0\right]_i \mid x_k\right)\right]\right]\right]
$$
where we first sample a datapoint $x_0$, sample a number of tokens to mask $k$ (either uniformly or
according to some schedule), then mask that many tokens at random and compute a cross entropy loss over those masked tokens. It turns out that a D3PM absorbing (\[MASK\]) model trained on the usual ELBO objective with the x0-parameterization reduces to a reweighted version of this MLM objective. Where the reweighting comes from the different weights assigned to different numbers of masked tokens $k$.

When we take into account that each unmasked token in a sequence has a KL-divergence of 0 since unmaksed cannot make any other transitions. Further more we can set the term to a constant in the KL-divergence that is responsible for mask transitions since this is independent of the models parameters $\theta$. Lastly if we take the $\beta_t=1/(T-t+1)$ schedule then we can even further simplify the objetive function to

$$
\min \left.-\mathbb{E}_{q\left(\boldsymbol{x}_0\right)}\left[\sum_{t=1}^T \frac{1}{t} \mathbb{E}_{q\left(\boldsymbol{x}_t \mid \boldsymbol{x}_0\right)}\left[\sum_{i \text { with }\left[\boldsymbol{x}_t\right]_i=m} \log p_\theta\left(\left[x_0\right]_i \mid x_t\right)\right]\right]\right]
$$

Note that while this looks very similar to Equation 11 (with each term reweighted by 1=t, the expected number of masked tokens) it is not exactly identical since masking is computed independently per token position (instead of choosing exactly k tokens to mask). This is an entirely practical way to do masking (and indeed some methods implement it this way). 

