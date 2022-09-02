# Face boundry and facial landmark detection

## Goal
<p float="center">
    <img src="Images/1.png" width="42%">
    <img src="Images/7.png" width="42%">
</p>

## Data set
[This data set](https://drive.google.com/file/d/1Jshwoo4KIDdCl_QkaWJ6HtGKC4JKOcU6/view?usp=sharing)
consists of 4275 images. Some images have multiple faces and some only have a person on it.

In this dataset, you can find annotations.txt which contains the labels including bounding box and landmarks annotations. The format of this text file is as follows (line by line):
* Path to image
* Number of faces in the image (n)
* For each face (n line): x y w h x1 x2 ... x68 y68 
    * x and y represent the top-left point of the bounding box
    * w and h are the width and height of the bounding box
    * (x1, y1) up to (x68, y68) are the 68 landmark positions in the face

## Notebook details

In [First notebook](./part1_face_boundary_detection.ipynb), I trained a vgg16 model with imagenet weights which has only two trainable layers. This model gets resized images of areas in images that selective search algorithm picked, then classify those resized parts into non-face and face categories. Also in this notebook I trained data with customized fit function. 

You can see the vgg16 structure used in this notebook below

<img src="Images/rcnn.png" width="40%">

[Facial landmark detection](./part2_facial_landmark_detection.ipynb)



You can see the cnn structure used in this part below

<img src="Images/rcnn.png" width="40%">

[Face boundry and facial landmark detection](./part3_face_boundary_and_facial_landmark_detection.ipynb)

## Refrences
[R-CNN implementation article](https://towardsdatascience.com/step-by-step-r-cnn-implementation-from-scratch-in-python-e97101ccde55)

[R-CNN implementation code](https://github.com/Hulkido/RCNN)

[Facial landmark detection code](https://github.com/LordLean/Facial-Landmark-Detection)

[Custom Fit](https://www.tensorflow.org/guide/keras/customizing_what_happens_in_fit)