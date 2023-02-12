# Galaxy Type Classification

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AlieNiT/Galaxy-Type-Classification/)

## Description
In this project, we trained 3 models on a dataset containing pictures of 4 types of galaxies, and compared the models.
I should also mention that this project is based on and inspired by an assignment in [this course](https://github.com/asharifiz/Introduction_to_Machine_Learning).

## Dataset
The datasset we're using in this project is [EFIGI](https://www.astromatic.net/projects/efigi/) dataset which contains 4458 images classified by their shape:


<p align="center">
  <img src="/Shapes.png" style="width: 100%" title="Samples from all classes">
</p>

* Ellipticals: 289 images
* Lenticulars: 537 images
* Spirals: 3315 images
* Irregulars: 317 images

As you can see, about 74% of the images are from one class and this bias in the dataset can cause unwanted behaviours in our models.

## Models
1. A MLP model with 3 hidden layers and CrossEntropyLoss: This approach can reach a pretty high accuracy(74%) in only one epoch. However, the model basically returns 2(Spiral) for any input image. This behaviour of the first model comes from the bias in our training set.
2. Same MLP model but with WeightedCrossEntropyLoss: In this trial, even though the accuracy didn't go very high, at least our model learned something and was able to predict samples from all classes.
3. CNN model with WeightedCrossEntropyLoss: The last model was a Convolutional Neural Network ([ResNet](https://en.wikipedia.org/wiki/Residual_neural_network)) which, with much less parameters, could achieve the same accuracy and even improve it slightly. The CNN model also prevents overfitting.

## Conclusion
* Bias in the dataset can have high impact on the model's traitability. In this case, the difference between frequencies of classes caused a big issue in the learning process.
* In image datasets, CNNs almost always outperform fully connected networks. In this case also, the 3rd model worked better than the other one.
