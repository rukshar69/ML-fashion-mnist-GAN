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

Since the GAN model consists of the generator and discriminator, a custom Model class *FashionGAN* is written that combines the Generator and Discriminator. *FashionGAN* also contains custom training step that updates the generator and discriminator by using separate optimizers and loss functions. So, we have 2 loss values to track *d_loss*(discriminator loss) and *g_loss*(generator loss).

Before training the model, a custom Callback class *ModelMonitor* is created to monitor the training progress and save some generated images using the trained generator at that epoch. This is done to check how the generator is evolving during training and evaluate its performance regarding fashion-item image generation.

The code for this training is in [fashion_mnist_GAN.ipynb](https://github.com/rukshar69/ML-fashion-mnist-GAN/blob/main/fashion_mnist_GAN.ipynb)

## Continuous Training Issue

Since GAN takes quite a few epochs(in many cases several thousand epochs) to train well i.e. generating good images and since I am training on Google Colab, there are some issues with continuous training. If the internet disconnects, the training stops. Also, the total training time can even take several days and this requires a person continuosly checking the training progress which isn't possible. Again, the usage limits of colab needs to be considered. For these reasons, I have modified the *ModelMonitor* callback class to  save the generator and discriminator weights after every epoch and also save the loss values. This allows me to run the model for some epochs and later I can reload the previously saved generator and discriminator weights to continue training from where it left off. Also, I generate 2 images after each epoch using the trained generator to check the performance of the model.

## References:
- [Keras custom callback methods](https://www.tensorflow.org/guide/keras/writing_your_own_callbacks#epoch-level_methods_training_only)
- [Fashion-GAN](https://github.com/nicknochnack/GANBasics/tree/main)