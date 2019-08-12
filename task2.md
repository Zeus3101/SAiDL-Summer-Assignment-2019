# Task 2 Computer Vision

First, I uploaded the data to the drive and mounted it onto colab. The first function, __create_pathlist()__ is used to generate a list of all paths. The output is a dictionary with three keys: train, val and test. Since each of the class has 25 groups under them, I've divided them accordingly: 1-20 in train, 20-21 in val and 22-25 in test. 

Next, I declared a custom _torch.utils.data.Dataset_ class __VideoDataset__. It takes the root directory path, the data split(train, val or test) and a transform as input. 
The method __video_read()__ is used to convert the video into a batch of 16 frames chosen randomly and read in order of their appearance. I used the OpenCV module for this. This method returns a set of images and their corresponding labels(which are the same).
The magic methods **__len()__**, **__iter()__** and **__next()__** have also been implemented suitably.
The magic method **__getitem()__** converts those images into a training compatible format. 

Then, I used a pretrained model VGG16 to classify these images. 

There are a number of things I'd like to improve in this. It is a very basic approach and due to some error, it doesn't deliver good accuracy. 
1. Refine the way the way the __video_read()__ method works so that each label corresponds to a video instead of individual images of the video. This is causing a problem and decreasing the accuracy of the network drastically.
2. Instead of making the classifier of the pretrained model a regular MLP, I wanted to try make it an RNN instead but couldn't get a clean implementation. 
3. Speed up the video capturing process by incorporating threading. That would basically let me process multiple videos simultaneously. Either that or process multiple images at the same time. I couldn't implement either because I couldn't learn it well enough to apply over here in the stipulated time.

### Note: There is an error in the way I'm calculating the accuracy right now. I'll only change that part slightly
