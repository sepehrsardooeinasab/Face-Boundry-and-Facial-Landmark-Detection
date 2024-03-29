# Face boundry and facial landmark detection

## The goal
<p float="center">
    <img src="Images/1.png" width="42%">
    <img src="Images/7.png" width="42%">
</p>

## The data set
[This data set](https://drive.google.com/file/d/1Jshwoo4KIDdCl_QkaWJ6HtGKC4JKOcU6/view?usp=sharing)
consists of 4275 images. There are some images with multiple people and some with only one.

In this dataset, you can find annotations.txt which contains the labels including bounding box and landmarks annotations. The format of this text file is as follows (line by line):
* Path to image
* Number of faces in the image (n)
* For each face (n line): x y w h x1 x2 ... x68 y68 
    * x and y represent the top-left point of the bounding box
    * w and h are the width and height of the bounding box
    * (x1, y1) up to (x68, y68) are the 68 landmark positions in the face

## Notebooks details
### First notebook
In [First notebook](./part1_face_boundary_detection.ipynb), A VGG16 model with Imagenet weights and only two trainable layers was trained. This model gets resized images of areas that selective search algorithm picks, then classifies those resized parts into non-face and face classes. Also in this notebook the model was trained by a custom fit function. 

<p float="center">
    <img src="Images/2.png" width="42%">
    <img src="Images/3.png" width="42%">
</p>

### Second notebook
In [Second notebook](./part2_facial_landmark_detection.ipynb), A CNN model was trained to estimate landmark positions on faces.

<img src="Images/4.png" width="70%">
<img src="Images/5.png" width="70%">

### Third notebook
In [Third notebook](./part3_face_boundary_and_facial_landmark_detection.ipynb), The results of the first trained model were given to the input of the second trained model, so it can detect faces boundries and facial landmarks.

In this notebook you can see all the steps taken.

## Problems
1. RCNNs are slow. It is better to use YOLO or other alghoritems.
2. In order to detect facial landmarks the second network needs a perfectly cropped face. Therefore, it is better to implement the first network as it calculates the boundary box loss.
3. Training 4275 images (which contains multiple faces) with quite large networks like VGG16 needs a lot of computional resourses. A lot more than resources available in free plan of Google collab which I used. 🙃

## The Models
The models used in the first notebook and the second one.

<p float="center">
    <img src="Images/rcnn.png" width="42%" valign='top'>
    <img src="Images/cnn.png" width="42%" valign='top'>
</p>

## References
[R-CNN implementation](https://towardsdatascience.com/step-by-step-r-cnn-implementation-from-scratch-in-python-e97101ccde55)

[R-CNN implementation](https://github.com/Hulkido/RCNN)

[Facial landmark detection](https://github.com/LordLean/Facial-Landmark-Detection)

[Custom Fit](https://www.tensorflow.org/guide/keras/customizing_what_happens_in_fit)