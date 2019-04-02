# **Behavioral Cloning** 

---

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report

## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/432/view) individually and describe how I addressed each point in my implementation.  

---
### Files Submitted & Code Quality

#### 1. Submission includes all required files and can be used to run the simulator in autonomous mode

My project includes the following files:
* model.py containing the script to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 
* writeup_report.md or writeup_report.pdf summarizing the results

#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```

#### 3. Submission code is usable and readable

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. An appropriate model architecture has been employed

CNN model used 3 5x5 filters with depth 24,36,48 respectively and then follows a 3x3 filter with a depth of 64 filters these is then flattened, and connected to 3 fully connected layers with each containing 100,50,10 neurons and finally output layer containing a single neuron that gives steering angle.

the correspond code can be found in second block of cell 1 in model.py file.

#### 2. Attempts to reduce overfitting in the model

The model contains dropout layers in order to reduce overfitting (line 70 of cell 1) and data is agumented to by flipping the images to avoid overfitting. 
The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track.

#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually (model.py line 73 in cell 1).

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road. I used a combination of center lane driving, recovering from the left and right sides of the road ... 

For details about how I created the training data, see the next section. 

### Model Architecture and Training Strategy

#### 1. Solution Design Approach

The overall strategy for deriving a model architecture was to ...

My first step was to use a convolution neural network model similar to the one discussed in class, I thought this model might be appropriate because 
1) it has sufficient filter to find different features.
Steps:
1) I collected the data by driving the car in training mode in different cases, trying to keep in center.
2) then after that i feed this data into cnn(design as discussed above), and also i agumented data by flipping and using left and right camera images with correction factor.
3) splitted this into training and validation (95%, 5% respectively ),
4) Trained on training set and validated using validation data set.
5) then saved the model and ran it in autonomous mode.

#### 2. Final Model Architecture

CNN model used 3 5x5 filters with depth 24,36,48 respectively and then follows a 3x3 filter with a depth of 64 filters these is then flattened, and connected to 3 fully connected layers with each containing 100,50,10 neurons and finally output layer containing a single neuron that gives steering angle.

the correspond code can be found in second block of cell 1 in model.py file.

#### 3. Creation of the Training Set & Training Process

1) To capture good driving behavior, I first recorded one laps on track one using center lane driving.

2) I then recorded the vehicle recovering from the left side and right sides of the road back to center 

3) I  flipped images and angles thinking to get more data