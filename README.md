# Generative model
According to different data and different task goals, this repositories lists four generative models I built.  
Including VAE, GAN, CNN-LSTM and Unet-SelfAttention.

## VAE model
The VAE model consists of two main components: an `encoder` and a `decoder`. 

The encoder takes input data, such as images, and maps it to a lower-dimensional latent space representation. The decoder then takes samples from this latent space and reconstructs the original data.  

During training, the VAE aims to minimize a loss function that measures the difference between the input data and the reconstructed data, while also encouraging the distributions outputted by the encoder and decoder to be similar to a predefined prior distribution (often a simple Gaussian distribution).
<div align="center">
  <img src="VAE/vae_structure.png" width="500" />
</div> 

### Task and Dataset
Generate similar images based on the given image.

`Dataset`: https://www.kaggle.com/datasets/salmaneunus/railway-track-fault-detection

### Performance
The upper line is the original image, and the lower line is the generated image.

<div align="center">
  <img src="VAE/reconstruction.png" width="500" />
</div> 

### Important concept

#### Training loss of VAE:  

Total loss = `Reconstruction loss` + 0.001 * `KL Divergence Loss` 

`Reconstruction Loss` = Use a pixel-level loss function, such as mean square error (MSE), to compare the difference between the input image and the reconstructed image generated by the model. 

`KL Divergence Loss` = This loss function measures the difference between the distribution of the latent space encoding learned by the model and the predefined prior distribution. 


## GAN model 
GAN consists of two main parts: generator and discriminator. 

`Generator`: Generate realistic data samples from random noise. It usually consists of a series of deconvolution layers and activation functions. 

`Discriminator`: The discriminator divides the input data samples into real data and generated data. It usually consists of a series of convolutional layers and activation functions, and its output is a probability value between 0 and 1, indicating the probability that the input data is real data.

<div align="center">
  <img src="GAN/GAN_structure.png" width="500" />
</div> 

### Task and Dataset 
Generate similar images based on the given image.

Dataset: `real_image` folder (More than 5,000 real images were used during the training process, and only 20 are given here for demonstration). 

### Performance 
The picture below shows the images generated by the trained GAN, and you can compare it with the real images for real_image folder. 

<div align="center">
  <img src="GAN/reconstruction.png" width="500" />
</div> 

### Important concept

#### Adversarial Training: 

The training of GAN is an adversarial process in which the generator and the discriminator compete and confront each other. The generator tries to generate realistic data to fool the discriminator, while the discriminator tries to differentiate between real data and generated data. This adversarial training method allows the model to gradually improve its capabilities and generate more realistic data samples.


## CNN-ConvLSTM model
ConvLSTM introduces convolution operations to enhance LSTM so that it can effectively process spatiotemporal sequence data. The basic idea is to combine convolutional layers and LSTM units to process both spatiotemporal and temporal information in a sequence. 

<div align="center">
  <img src="CNN_LSTM/convLSTM.png" width="300" />
</div> 


### Task and Dataset
Given satellite images from a particular storm, the model should generate 3 future satellite images at 3 given future timestamps.

`Dataset`: The training dataset consists of satellite images of 30 tropical storms around the Atlantic and East Pacific Oceans. Each storm has a varying number of time samples with irregular time intervals.

Example data are in the `data` folder. 

<div align="center">
  <img src="CNN_LSTM/data/tst_000.jpg" width="200" />
</div> 




## Unet-Self Attention model

