# Malaria Diagnosis Using Convolutional Neural Networks on Thin Blood Smear Images
Malaria is a life-threatening disease which has claimed a lot of lives in the past
and is still considered as one of the most life-threatening diseases. It is commonly
diagnosed by taking blood samples from patients and preparing slides which are
then observed by experts under a powerful microscope to check for infected cells.
The blood samples are taken several times and are sent to laboratories for expert
examination. This is a time-consuming process which involves manual intervention.
Computer vision has proven to be very helpful in many image classification and
object detection problems. Machine learning and deep learning are nowadays widely
used to solve many real-life problems which is achieved by training these algorithms
up to an extent after which they can identify and classify images. This research
project uses thin blood smear images and aims to build deep learning models to
identify whether any of the blood cells are infected by malaria parasite or not.
First a normal CNN model has been built to classify images in two categories i.e.
Infected and Healthy followed by Resnet50 for same purpose. After this, Faster
RCNN has been implemented for detecting infected blood cells.

## Problem Statement ##

Keeping the long-term complete malaria elimination goal in mind, it has become necessary
to not just only develop new vaccines and drugs but also develop new efficient methods
to diagnose malaria. Malaria diagnosis is time taking and involves taking multiple blood
samples from patients in a course of multiple days. Computer vision nowadays is widely
used in many practical situations for the purpose of classifying images or detecting an
object. This research project intends to use these technologies for finding out malaria
infected thin blood smears and is an attempt towards diagnosing malaria using deep
learning in near future.

## Research Questions: ##

*Research Question 1*: "Can deep learning models help diagnose malaria by applying
computer vision technology on thin blood smear images?"

*Research Question 2*: "Can this research achieve presentable results for a small sample
of images?"


## Dataset Used: ##

Data used in this project contains P. vivax infected human blood smears images. The images
contain four classes of infected cells (gametocytes, rings, trophozoites, and schizonts)
and two classes of healthy cells (RBCs and leukocytes). A total of 1364 images were
downloaded from Broad Institute website.

https://data.broadinstitute.org/bbbc/BBBC041/

## Data Preparation ##

Data preparation which in this research project is image pre-processing is one of the most
important steps. Image pre-processing for this project works in a loop as also mentioned
in the CRISP-DM methodology. There are a series of operations which were performed
on the images before feeding them in our CNN models. As this project uses CNN models
for classifying the blood smear images in two classes i.e. Infected, Uninfected and also
uses Faster RCNN for detecting infected blood cells in the images, so two different sets
of image pre-processing were required to do, one for the purpose of classifying images
and another for detecting infected blood cells in images. There are few pre-processing
steps which are common in both types of pre-processing done like applying gaussian blur.
When the dataset was downloaded, all the images were present in a single folder and two
csv files were also downloaded. After pre-processing, all images present in same folder
setup was used as it is for CNN and ResNet-50 models for classification purpose. For
implementing Faster RCNN, these images were first separated in two different folders i.e.
Train and Test. It was later noticed that the test images look different from the train
images, so just for the task of detecting infected blood cells accurately, few images in
test folder having bounding box co-ordinates were moved to train folder and vice-versa
so that the model is trained to detect accurately.

For the approach of classifying images, all the images were resized to 224, 224. The
images were then cropped into a circular shape. To tackle the problem of class imbalance
and smaller number of images for training the models, all the images were rotated by
certain angles which summed up to 4075 images as shown below:

| Classes        | Train           | Test  |
| ------------- |:-------------:| :-----:|
| 0(Uninfected)      | (189 images x 10 angles) 1890 | (3 images x 10 angles) 30 |
| 1(Infected)      | (1019 images x 2 angles) 2038      |   (117 images x 1 angle) 117 |

For our second approach which is about detecting infected cells in blood smear images, original number of images were used i.e. 1364. Here it was noticed that train images
had different size as compared to test images, so all the test images were reduced to
width=1600, height=1200 from width=1944, height=1383. It was also noticed that the
test images look a little different from the train images which might cause a problem while
detecting infected cells in test images as stated above. Additionally, all the train and test
images were then converted to grayscale and then GaussianBlur was applied using cv2
in python to make them look a little similar. After this pre-processing all images were
stored in a single folder from where they were pulled and and stored in two different
folders i.e. Train and Test folders.
