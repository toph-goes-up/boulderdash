% Boudlerdash
% Christopher Kinsey A01784086
% USU CS 5600 Project 2 Proposal

#Boulderdash

## Description
Rock climbing walls can be very visually cluttered. This project will use modern deep learning methods to recognize climbing holds on an indoor rock wall. Recognized holds could then be grouped into routes with clustering techniques and an an overlay could be drawn to highlight all the holds on a route, simplifying the process of visually tracking down all the holds needed in a climb. 

Recognizing holds will be an image segmentation problem. Convolutional neural networks have been applied to this problem to great success, so that is the method I will be using. Unlike the ConvNets done earlier in this class, this problem requires a segmentation map for output, which will be an image. This means that the final few layers of the network will be convolutional rather than fully connected.

Grouping the holds into routes will likely not need to be done by a neural network, so that will be a stretch goal for now. 

## Resources
The data to train this network does not yet exist to the best of my knowledge. This means that I will have to harvest the training data myself. Training data for an image segmentation network consists of two parts:

1. Raw images of the wall. These will be the input X vectors.

2. Segmentation maps corresponding to the input images. These will be the ground truth y vectors.

Climbing walls are usually neutrally colored walls with brightly colored holds. This should make the problem easy enough to solve without an enormous amount of training data. I will take photos of different indoor walls and manually trace over them to get the ground truth segmentation maps. 

Segmentation nets can either be trained directly, or in two steps. The first step is training it with isolated picted of the segments. In this case, that would be a small section of the big image with a single hold near the center. The second step is to train it on the full size picture, with seperate segments all over the image. I will try to train it directly in a single step first, but if I don't get satisfactory results I will try again with two step training.

I plan to use CV2 and TFLearn for this project. I'll test out a few different structures for the networks. In particular, I want to try out the Inception module architectures first implemented in GoogLeNet for the ImageNet competetion (TODO: ADD LINK)

Once I have harvested the images and made the ground truth maps, I will upload them to my project repository at github.com/tophski/boulderdash.

## Deliverables

- Trained and persisted TFLearn models with code to run them.

- Source code that I used to create the networks. 

- Images and segmentation maps used for training and testing.

- Segmentation maps produced by the networks, overlaid on their corresponding images.

- A report on the results.

## Tentative Schedule

- Tuesday, 13 November: Take pictures of at least one two climbing wall. Preprocess images into standard sizes.
- Tuesday, 20 November: Try to get pictures of more walls if other gyms will allow it. Trace over the images to create training / testing segmentation maps.
- Tuesday, 27 November: Preprocess the images. Train and test one neural network. This week will mostly be setting up the training and testing utilities.
- Tuesday, 4 December: Test ten more neural network architectures. Collect data and prepare it for a report.
- Tuesday, 11 December: Write report and present results.
- Thursday, 13 December: Clean up project and submit everything.

## Risks

The primary risk of this project is that my computing hardware will not be powerful enough to train a convolutional segmentation architecture. If this ends up being the case, I will try to borrow computing power from friends, but I will stil likely not be able to test as many architectures as I want to in the given timeframe.

The other main risk that I forsee is not having enough training data. Curating the training data myself will be time intensive, so if I do not have enough of it by I start training, it will be hard to gather and prepare more images in time to train the networks.


