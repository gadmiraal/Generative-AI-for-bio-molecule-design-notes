## Terminology
- **Equivariance** means that the order of operations does not contribute to the end result. An example is the plus and minus operation, if we wanted to add and subtract a bunch of numbers it does not matter in which order we add or subtract the end result will still be the same. For neural networks this could mean that if the input is changed by some operation then the output is also changed equivalently by this operation
- **Invariance** is often confused with equivariance but are not the same. Invariance means that the output does not change depending on how the input is transformed. A classifier should still classify an image the same even tough the image might be rotated or translated
## Equivariant Models (EM) vs. Data Augmentation
Equivariant Models are designed to respect and leverage symmetries present in the data. Equivariance in the data can also be addressed by using data augmentation but this is often not as data efficient and not all kinds of operations can be used during data augmentation. Additionally, data augmentation is often only used on the input layer whereas EMs are equivariant in all layers. Lastly, EMs have a better generalizability at the expense of less expressivity and use weight sharing to reduce the number of parameters.
## Group Equivariance
Group Theory is a branch in mathematics that targets the study of groups. A group is defined by a set of elements and a binary operation that can be exerted on the set elements. Such an operation is done on two elements of the group which then must result in an element that is already present in the group. Groups are used to analyse symmetries, transformations and patterns in various scientific contexts. Group theory can thus be used to enforce equivariance in Neural Networks
#### Group Examples
- Translation group $(\mathbb{R}^2, +)$ which consists of all possible translations in $\mathbb{R}^2$
- Rotation-translation group $SE(2)$ which consists of the coupled space $\mathbb{R}^2\times S^1$ that combines a 2D translation vector with a scalar rotation value
- Scale-translation group $\mathbb{R}^2\rtimes \mathbb{R}^+$ which consists of the coupled space $\mathbb{R}^2 \times \mathbb{R}^+$ that combines a 2D translation vector with a scalar rotation value
- $E(3)$ is the group of rotations, reflections and translations in 3D space
- $SU(2)$ <span style="color:#ff0000">???</span>
## Transformers and Graph Neural Networks (GNN)
Transformers and GNN are both permutation equivariant since they do not care for the order or size of the input but are not rotation equivariant. 

<span style="color:#ff0000">Add more!!!</span>
## Use cases
EM is especially useful and has been used in the analysis of medical images using Group Convolutional Neural Networks. Additionally, the equivariant transformer plays an important role in the [[AlphaFold]]-2 paper [[Jumper, John, et al. Highly accurate protein structure prediction with AlphaFold.pdf]]. Generally many molecular applications seem to benefit from equivariant prius. EM can help better model and predict DNA data since DNA as an inherent symmetry.

## Resources used
- [Wikipedia article on equivariance](https://en.wikipedia.org/wiki/Equivariant_map)
- ![](https://www.youtube.com/watch?v=2bP_KuBrXSc)
- ![](https://www.youtube.com/watch?v=RBKERHaiEKY)
