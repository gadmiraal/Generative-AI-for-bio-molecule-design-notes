## Introduction
When generating outputs, say images, from a [[Diffusion Model]] it is desirable to incorporate class labels and thus guide the model to give outputs that exhibit these class labels. This means that we can make our model output for example an image of a dog. There are currently three main ways to guide these diffusion models; classifier guidance, classifier-free guidance and gradient-guidance, which will be further explored below.
## Classifier Guidance
Classifier guidance involves using an external classifier to provide feedback or guidance during the generative process. This classifier can be a pre-trained model used to evaluate the quality of generated samples based on specific criteria. The goal is to condition the generation process on this classifier's feedback to produce more realistic or desired outputs.

When using classifier guidance we use an additional classifier to guide the denoising model to the correct class label. A classifier $p(y|x)$ tries to model/fit a high-dimensional input $x$ to a target label $y$. Using this approach we turn an unconditional diffusion model into a conditional diffusion model.

In the paper [[Dhariwal, Prafulla, et al. Diffusion Models Beat GANs on Image Synthesis.pdf]] they incorporate class information in two ways. The first being that that the class information is used into the normalization layers thought the use of Adaptive Group Normalization (see [[Diffusion Model]]). Secondly, they exploit a classifier to improve the diffusion generator. They achieve this by using the gradient of the log probability $\log p_\phi(y|x)$ of a target class $y$ predicted by the classifier $\psi$. Additionally a scaling factor $\gamma$ is used on the conditioning term in the scoring function. When this scaling factor is larger than one it has the effect of amplifying the conditional signal $$ \nabla \log p_\gamma(x|y) = \nabla_x \log p(x) + \gamma \nabla_x \log p_\phi(y|x) $$
Some drawbacks for this method is that in order for the classifier to work with noise it has to be trained with highly noisy images. This means one cannot use an off the shelf classifier and a separate one must be trained. Another inherent drawback is that since the input $x$ almost always has noise which does not contribute to the relevancy of predicting a class label $y$. This results in that the calculated gradients can yield arbitrary directions in the input space which is not desirable. 
## Classifier-Free Guidance
Classifier-free guidance, also known as unconditional diffusion, doesn't rely on an external classifier for guidance. Instead, it focuses on improving the generative process using purely probabilistic techniques.

One of the first to successful adoption of classifier-free guidance was by [[Nichol, Alex, et al. GLIDE Towards Photorealistic Image Generation and Editing with Text-Guided Diffusion Models.pdf]] and they do not use a separate classifier but instead train a conditional diffusion model with **conditioning dropout**. With conditioning dropout some percentage of time $(10\%-20\%)$ the condition information $y$ is removed and replaced with a special input value $\emptyset$ representing the absence of conditional information. Thus during the backwards process you can the input at a given time $t$ in twice, once with class embedding and once without. We can then calculate the difference between the two outputs and use this difference. You amplify it again by a guidance scaling factor $\gamma$ and use it to steer the network into the desired class direction. Additionally, this allows the model to function as a conditional model $p(y|x)$ and as an unconditional model $p(x)$. 
The scoring function now looks like this, where $\gamma$ is again the guidance scaling factor $$\nabla_x \log p_\gamma(x|y)=(1-\gamma) \nabla_x\log p(x) + \gamma \nabla_x \log p(x|y)$$
When $\gamma$ is set to 0 we have a fully unconditional model and when it is set to 1 we have a fully conditional model. Magic thing happen when we set $\gamma >  1$ see the images below

![panda1](https://sander.ai/images/panda1.jpg)
*A set of samples from OpenAI's GLIDE model, for the prompt 'A stained glass window of a panda eating bamboo.' Guidance scale 1 (no guidance)*

![panda2](https://sander.ai/images/panda3.jpg)
*A set of samples from OpenAI's GLIDE model, for the prompt 'A stained glass window of a panda eating bamboo.' Guidance scale 3*

In a way a 'classifier' is constructed from a generative model. This is because standard classifiers can take shortcuts and ignore most of the input while still obtaining good classification results. Generative models cannot do this making their gradients more robust.

One downside to using guidance is that the resulting output comes at a cost of diversity. In conditional generative model this can be an acceptable trade-off since the diversity can also come from the conditional signal.
## Gradient Guidance
Gradient guidance, also known as autoregressive guidance, leverages gradient-based optimization techniques to guide the generative process. It is commonly used in models like autoregressive generative models and autoregressive flow models.

From [[Gruver, Nate, et al. Protein Design with Guided Discrete Diffusion.pdf]] 
	Gradient guidance typically augments sampling from a generative model with gradient steps to increase the occurrence of a desired attribute [53]. Gradient guidance is natural within the framework of continuous diffusion models [20], and Li et al. [47] use this connection to perform gradient-guided sampling from a diffusion language model. To obtain a continuous space, they perform Gaussian diffusion [38] on word embeddings, decoding out to tokens using a linear head. The original method required many careful engineering interventions, e.g. clamping latent representations to the nearest word embedding, that have been improved by recent methods, such as CDCD [21], but gradient guidance has not been discussed for these more recent formulations.

Also
	To achieve a similar form of gradient guidance without carefully engineering a latent space, Dathathri et al. [17] and Yang and Klein [79] propose gradient-guided autoregressive models by using the decoder’s activations as a gradient-friendly latent space. These methods alternate between sampling from logits and ascending the likelihood of a separately trained classifier model. Surprisingly, despite work on gradient guidance for continuous noise diffusions and autoregressive language models, there has been little work on gradient guidance for general categorical diffusions that predict denoised categorical distributions (e.g. CMLM, SUNDAE, CDCD), which is a topic we explore in detail.

## Resources Used
- https://sander.ai/2022/05/26/guidance.html
- ![](https://www.youtube.com/watch?v=1CIpzeNxIhU)
- ![](https://www.youtube.com/watch?v=gwI6g1pBD84)