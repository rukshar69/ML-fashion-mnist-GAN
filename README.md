# ML-fashion-mnist-GAN
GAN model to generate clothing images trained from fashion mnist dataset

## Fashion MNIST Dataset
The Fashion MNIST dataset is a popular machine learning dataset used for image classification tasks. Fashion MNIST consists of 60,000 grayscale images of 10 different clothing items and accessories, with each class representing a distinct fashion category. These categories include items like t-shirts, dresses, sneakers, and more. Each image in the dataset is 28x28 pixels in size, making it a 28x28 binary pixel image classification problem. Fashion MNIST is frequently employed for benchmarking and testing machine learning algorithms and models, particularly in the context of computer vision and deep learning. It provides a diverse and slightly more complex dataset than the original MNIST, making it a valuable resource for developing and evaluating image classification algorithms.

In the code, *tensorflow_datasets* library is used to load the dataset. We normalize the images by dividing by 255.0. The dataset is divided into batches of 128 images per batch.

## Model Architecture
There are 2 parts of GAN model: Generator and Discriminator.

**Generator**

![Generator](https://github.com/rukshar69/ML-fashion-mnist-GAN/blob/main/Images/generator.png)

**Discriminator** 

![Discriminator](https://github.com/rukshar69/ML-fashion-mnist-GAN/blob/main/Images/discriminator.png)

## References:
- [Keras custom callback methods](https://www.tensorflow.org/guide/keras/writing_your_own_callbacks#epoch-level_methods_training_only)
- [Fashion-GAN](https://github.com/nicknochnack/GANBasics/tree/main)