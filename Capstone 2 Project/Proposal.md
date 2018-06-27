# Capstone Two Project Proposal

**Title:** Object Detection From Video

**Problem:** It seems like we are always sitting in front of screens these days. Computer screens, movie screens, phone screens, etc. are just some of the daily few we interact with. But what if we could do more than just watch? What if we maximized the business and personal interactivity potential with our screens? How many times have you been watching a tv show or movie and loved a character's outfit, car or some kind of gadget? Don't you wish you could just touch it on the screen and your web browser opens up amazon with that exact item for purchase. For the business oriented people, wouldn't you like to maximize the potential of your ads reaching your target customer? Imagine marketing that can "see" what your customer's are watching and only show them ads or products relative to their viewing likes. A person who is always watching football, baseball, and sports related movies might be more interested in a commerical advertising the current sale going on at Dick's than they would at Sephora. Targeted demographic marketing and other capabilities could be improved exponentially if our screens could see the things we are seeing and know what they are. This would need to grow from the foundation of accurate object detection in Video.

**Who might care?** The following could be a potential target of this type of technology and isn't all inclusive:
* Consumers who see something and would want to buy instantly by simply touching the screen. This ideally would trigger an image search which would return either the exact item or something similar
* People who desire interactiving information e.g. as the simplest example, touching the face of an actor and their imdb page populates
* Businesses who want to better reach their targeted demographic. With the tech recognizing and keeping details on what the user is watching, statistics could be aggregated on what type of ads they'd be more inclined to watch instead of flipping the channel

**Data:** ImageNet, who sponsors a yearly competition has aggregated over 500gb of labeled video. This can be utilized for model training

**Modeling approach:** Dealing with images and videos is no simple task. Computer vision is still in it's infacy stages relative to the technology word. However there is a very powerful library that can be used to facilitate computer vision processing. Utilizing OpenCV with Python (possibly C++ depending on optimization needs), data will be fed into a deep convolutional neural network in order to train a object detecting model in video.

**Possible limitations:** The amount of data might be too cumbersome to store locally. Initially a model will be trained on a subset of the data ~80gb. However if performance is too low on the models and more data needs to be used in the training process, cloud computing might have to be utilized. 

**Deliverables:** 
1.    Codes (notebooks) for:

	a. Data Preprocessing
	
	c. EDA - Exploratory Data Analysis and Feature Engineering
	
	d. Tensorflow Convolutional Neural Network
	
2.    Report on the capstone project
3.    Presentation on the capstone project
