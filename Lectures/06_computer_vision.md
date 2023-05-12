# Image Classification

## Computer Vision Tasks
- Image classification
- Object detection
- Semantic segmentation
- Instance segmentation
- Pose estimation
- Optical Character Recognition (OCR)

### Image Classification, Object Detection, Semantic Segmentation, Instance Segmentation
![](https://miro.medium.com/v2/resize:fit:800/1*rgliupBanbeMYW7xXYH5Lw.jpeg)

### Pose Estimation
![](https://learnopencv.com/wp-content/uploads/2022/10/yolov7-mediapipe-human-pose-detection-feature-1.gif)

### Optical Character Recognition (OCR)
![](https://uploads-ssl.webflow.com/61e7d259b7746e3f63f0b6be/620a5c708d332d551122939f_c9d501_5878f947e7c2455a8c423e738449f086_mv2.png)

### Problems
![](https://cs231n.github.io/assets/challenges.jpeg)

### CNN (Convolutional Neural Network)
![](https://cs231n.github.io/assets/classify.png)


## How do we assess the performance
- **Score function** (map raw data to class scores)
- **Loss function** (quantifies the agreement between the predicted scores and the ground truth labels)

### Determining the mode larchitecture base on the output dimension of what we sould like to accomplish
- In a **classification** tasks, the output later may consist of multuple neurons, each corresponding to a class label. Where each neuron is the probability of the input image belonging to the corresponding class. The output layer is usually a **softmax** layer, which is a generalization of the sigmoid function to multiple dimensions. The softmax function squashes the outputs of each neuron to be between 0 and 1, just like a sigmoid function. But it also divides each output such that the total sum of the probabilities is equal to 1.
- In a **regression** tasks, the output layer usually consists of a single neuron, which is the predicted value of the input image. The output layer is usually a **linear** layer, which is simply a neuron with no activation function.
- In a **object detection** tasks, the output layer usually consists of multiple neurons, including additional layers for generating bounding boxes and class labels. 
- In **semantic segmentation** tasks, the architecture may consis of an encoder-decoder network structure wuth skip connectons to preserve spatial information resulting in a pixel-wise classification of the input image.


### Image Classification
- **Input:** unage
- **Output:** single category for the image
- **Architecture:** CNN
- **Why is this interesting:**
    + Useful for image organization, search, and classification
    + Simple input and output specification
    + Requires reasoning about the entire image
    + Useful high-level proxy task to learn good representation which transfer to new tasks
    + Given a big dataset we can train a representation and take that model and fine tune it on another task --> get dewer data on the target task b/c we have pretrained on a much larger dataset