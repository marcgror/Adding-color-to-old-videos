One of the hottest topics in Deep Learning are GANs. In this project, we build a GAN based off in Pix2Pix to train it in a very ambicious task: transform grayscale images in RGB (3 channels) images. This will be interesting, as we will see, when trying to add color to old videos that were recorded in grayscale.

# Introduction

The main goal of this project is to bring color to old videos. Thus, we will use two videos while training ( one for train and one for test) and we will try the model in an old video (a record from Titanic, not the film).  We proceed as follows:
- first, split the original videos in frames, and store them for preprocessing. Now we have train and test images.
- apply the preprocessing on the images: resize, crop, normalize...
- get a copy of each image but in grayscale. Now we have two copies of each image: RGB and grayscale.
- build the dataset, where X (input) correspond to grayscale images and y (targets) correspond to color images.
- train the GAN on the dataset, showing it how we want the image to be (RGB).
Once we have the model trained, we can test it in another video the GAN has never seen. This is done in the test_colorize.ipynb notebook.

# Details
For computational purposes, each frame in the videos is resized and croped to 256x256.
The GAN model is exactly the same as the introduced in https://www.tensorflow.org/tutorials/generative/pix2pix#top_of_page. I have only modified the Generator to accept grayscale inputs (256, 256, 1), as we want the inputs to be grayscale images, not RGB.
Apart from this, the model remains unchanged.

# Improvements
- training for a lot more epochs. 60 maybe a poor number, but it take several hours in my computer.
- train with a more diverse training images. The results look a bit reddened, maybe because the training images present situations were red was the main color.
- when spliting the training video, select a larger number of fps, which allows to get more 'distanced' images and hence a better training.

# Results
The videos used and generated in this project are available:
- train: input_video.mp4
- test: test_video.mp4
- validation video: val_video.mp4
- generated video from val_video: colorized_video.mp4
