# Generative-Adversarial-Networks-GAN
**Generative Adversarial Networks with FashionMNIST-Dataset**

In principle, a GAN consists of two deep learning networks that operate in an adversarial relationship.

In this context, the generator network will generate imitations or fakes of images, while the discriminator network will try to distinguish the fakes from real images.

The generator has the task of taking a random noise as input and transforming this into an imitated image. 
The discriminator- a binary classifier that distinguishes real from fake images.

Over the series of training rounds, the generator gets better at producing convincing fakes and, correspondingly, the discriminator improves its ability to recognize the fakes. As the training progresses, the two models battle it out and try to outdo each other.

Training a GAN consists of two opposing processes:
1. discriminator training:
As shown in the figure below, in this process the generator produces imitations of images, i.e., it performs inference only.


![Figure 1: overview of the discriminator training loop!](https://github.com/TalhaFilikci/Generative-Adversarial-Networks-GAN-/blob/main/figure_1.PNG?raw=true)


2. generator training:
The discriminator evaluates the imitations produced by the generator. Here, it is the discriminator that performs inference only, while the generator uses this information to learn.


That is, in either process, one of the models produces its output (either a fake image or a prediction about whether the image is fake), but do not train; and the other model uses the output to learn to do its task better.

During the entire training process, generator training interchanges with discriminator training. 

Let's take a closer look at both processes, starting with discriminator training (see Figure 1).

- The generator produces imitated images. These imitations are mixed with batches of real images and fed into the discriminator for training.
- The discriminator outputs a prediction corresponding to the probability that the image is real.
- Cross entropy costs are calculated for the discriminator's predictions compared to the true labels.
- Using backpropagation tuning of the discriminator's parameters, the cost is minimized to train the model to better distinguish the real images from the fake ones.

During the discriminator training only the discriminator learns! The generator network is not involved in the backpropagation and therefore does not learn anything.

Let us now turn to the process that alternates with discriminator training: generator training (see Figure 2):

- The generator receives a random noise vector as input and generates an imitated image as output.
- The imitated images produced by the generator are fed directly into the discriminator. Crucial to this process is that we declare all the fake images to be real ones.
- The discriminator outputs predictions as to whether a given input image is real or fake.
- Cross-entropy costs are used here to fine-tune the parameters of the generator network. By minimizing this cost, the generator learns to produce fakes, which the discriminator falsely labels as true.

How good the images become from the generator after each epoch can be seen in the figure below. After the first run, the discriminator loss is 0.6676 and the generator loss is 0.715.
After 50 epochs the discriminator loss is 0.5312 and the generator loss is 0.934.



