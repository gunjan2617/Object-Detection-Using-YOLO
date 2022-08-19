# Object Detection Using YOLO
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

<img src="https://user-images.githubusercontent.com/88222317/185391657-8acd2b08-3622-4a24-a66a-d49f7509321e.png" width="600" height="250" />

Image Source: [ You Only Look Once: Unified, Real-Time Object Detection](https://pjreddie.com/media/files/papers/yolo_1.pdf)

* **Loss Function:** The  YOLO v1 Loss Function is divided into 4 parts:
  * Box Loss: Mean squared error of the predictions of the coordinates of midpoint (x, y) and the width and height of the bounding box (w, h).
  * Object Loss: Mean squared error of the probability that an object is present in the cell or not.
  * No Object Loss: Mean squared error of the probabilty that an object is not present in the cell.
  * Class Loss: Mean squared error of the predictions of the class probabilities of the object.
  
  
<img src="https://user-images.githubusercontent.com/88222317/185396853-058b5ae3-3b34-435d-bd3c-d0d8fa5b313b.png" width="600" height="300" />

Image Source: [ You Only Look Once: Unified, Real-Time Object Detection](https://pjreddie.com/media/files/papers/yolo_1.pdf)

 * Mean Average Precision: The Average Precision (AP) is calculated as the area under the Precision-Recall curve for a set of predictions per class. The average of this value taken over all classes called mean Average Precision (mAP) is calculated.
 
 ### Libraries used:
 * PyTorch
 * NumPy
*  Matplotlib
* Pandas

### Dataset used:
The PASCAL VOC Dataset was downloaded from [Kaggle](https://www.kaggle.com/datasets/734b7bcb7ef13a045cbdd007a3c19874c2586ed0b02b4afc86126e89d00af8d2).

### Parameters used:
Parameters  | Values
------------- | -------------
Learning Rate  | 1e-4
Batch Size | 16
Weight Decay  | 5e-4
Epochs  | 200
Optimizer  | Adam

### Results:

<img src="https://user-images.githubusercontent.com/88222317/185518293-bb237303-f251-4e35-b8f7-9170994983f9.png" width="600" height="600" />

As can be seen, YOLO imposes strong spatial constraints on bounding box predictions since each grid cell only predicts two boxes and can only have one class. This spatial constraint limits the number of nearby objects that the model can predict. It struggles with small objects that appear in groups, such as flocks of birds or crowds of people.

Parameter  | Result
------------- | -------------
Train mAP | 0.999009
Mean Loss | 6.133301

## Further Work on this Project:
Currently working on the YOLO v3 implementation of Object Detection on the PASCAL VOC Dataset to train the model to a decent level of accuracy and be able to visualise the output.

## References:
* [You Only Look Once: Unified, Real-Time Object Detection](https://pjreddie.com/media/files/papers/yolo_1.pdf)
* [YOLO v1 from Scratch by Aladdin Persson](https://www.youtube.com/watch?app=desktop&v=n9_XyCGr-MI)
* [YOLO: Real-Time Object Detection Explained](https://www.v7labs.com/blog/yolo-object-detection)
* [Introduction to YOLO Algorithm for Object Detection](https://www.section.io/engineering-education/introduction-to-yolo-algorithm-for-object-detection/)



