# Object-Detection-Using-YOLO
In this project, we will use the YOLO algorithm on the PASCAL VOC Dataset to detect real-time objects.

## Introduction:
The recognition and localisation of items in an image that belong to a predetermined set of classes is the focus of the Computer Vision technology known as object detection. A neural network is trained to anticipate items in an image in the form of bounding boxes in this more complex kind of image categorization. A cutting-edge object detection technique called YOLO (You Only Look Once) uses convolutional neural networks to identify things in real time. It is well-liked because of how quick and precise it is. It generates predictions for all of the class probabilities and bounding box characteristics of an image in a single forward propagation through the CNN. Therefore, YOLO!

### Working of the YOLO Algorithm:
* Splitting the input image into an SxS grids.
* The grid cell that contains the object's midpoint will be responsible for detecting it.
* Each grid cell outputs a prediction with B Bounding Boxes and provides their corresponding scores.
* The Bounding Box is in the form of [x, y, w, h], where (x, y) are the coordinates of the object midpoint in the cell relative to the cell and (w, h) is the width and height of the object also relative to the cell.

