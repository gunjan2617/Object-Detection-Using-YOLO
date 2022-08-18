# Object-Detection-Using-YOLO
In this project, we will use the YOLO algorithm on the PASCAL VOC Dataset to detect real-time objects.

## Introduction:
The recognition and localisation of items in an image that belong to a predetermined set of classes is the focus of the Computer Vision technology known as object detection. A neural network is trained to anticipate items in an image in the form of bounding boxes in this more complex kind of image categorization. A cutting-edge object detection technique called YOLO (You Only Look Once) uses convolutional neural networks to identify things in real time. It is well-liked because of how quick and precise it is. It generates predictions for all of the class probabilities and bounding box characteristics of an image in a single forward propagation through the CNN. Therefore, YOLO!

### Working of the YOLO Algorithm:
* Splitting the input image into an SxS grids.
* The grid cell that contains the object's midpoint will be responsible for detecting it.
* Each grid cell outputs a prediction with B Bounding Boxes and provides their corresponding scores.
* The Bounding Box is in the form of [x, y, w, h], where (x, y) are the coordinates of the object midpoint in the cell relative to the cell and (w, h) is the width and height of the object also relative to the cell.
* The ouput predictions of each cell are encoded as follows: [S x S x (5*B + C)], where C is the number of class probabilities.
* To evaluate YOLO on PASCAL VOC, we use S = 7, B = 2 (for Wide and Tall Bounding Boxes). PASCAL VOC has 20 labelled classes so C = 20. Thus, the final prediction is a 7 × 7 × 30 tensor.
* **Intersection Over Union:** A popular metric to measure localization accuracy by dividing the intersecting area of the bounding box and ground truth box with the area of its union. Larger the IOU, better is the prediction.
* **Non Maximal Suppression:** Since multiple cells can contain one object and each of them would predict their bounding boxes for it, NMS threshold is used to suppress those bounding boxes with lower confidence scores.
* **Model Architecture of YOLO v1:** The detection network has 24 convolutional layers followed by 2 fully connected layers. Alternating 1 × 1 convolutional layers reduce the features space from preceding layers. The size of the input image is 448 x 448 x 3, which eventually comes down to 7 x 7 x 30.

<img src="https://user-images.githubusercontent.com/88222317/185391657-8acd2b08-3622-4a24-a66a-d49f7509321e.png" width="800" height="300" />


