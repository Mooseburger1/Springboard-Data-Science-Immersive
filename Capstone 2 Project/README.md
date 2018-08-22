# Exploring Computational Efficiency in Object Detection with Convolutional Neural Networks
-------------------------------------------
<img src = 'https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%202%20Project/images/cnn%20output.png'></img>


This project spawned out of necessity and frustration. The original project was going to be an attempt at the Imagenet Object Detection Challenge. However I quickly ran into roadblocks that served as the pivot point for the focus of this study. Image and videos are expesnvie. No not monetary wise, but computationally and memory wise. In attempts to run early models, I kept crashing my kernel and waited for hours on hours for models to train. And from these struggles comes this investigation into improving computational effeciency in training CNNs using low level Tensorflow

### REQUIREMENTS
* OpenCV
* Tensorflow
* Tensorboard


OpenCV was used in this project for image vectorization and transformations. It is a comprehensive Python and C++ image/video processing library. There's a notebook with a quick reference and tutorial on how to use OpenCV for image and video capturing / processing seen [here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%202%20Project/OpenCV%20Basics%20and%20Tutorials.ipynb)

The data was 4000+ images from the ImageNet 2013 database and were preprocessed then stored to H5 files fro quick referencing. All work, code, thought process and explanation can be found on this [Jupyter Notebook](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%202%20Project/Convolutional%20Network/Tensorflow%20%20CNN%20Object%20Detector.ipynb)

The final report PDF can be read [here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%202%20Project/Report/Exploring%20Computational%20Efficiency%20in%20Object%20Detection%20with%20Convolutional%20Neural%20Networks.pdf)

If you're familiar with Tensorboard, all log files were saved [here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/tree/master/Capstone%202%20Project/Convolutional%20Network/tf_logs) for viewing

<img src='https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%202%20Project/images/tensorboard.png'></img>
