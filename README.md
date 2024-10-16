
# DETR (End-to-End Object Detection) with ResNet-50 Backbone
## Overview
**DETR (Detection Transformer)** is an end-to-end object detection model that utilizes a transformer architecture. Unlike traditional object detectors, DETR simplifies the detection pipeline and eliminates the need for components like region proposal networks and anchor boxes. This repository implements DETR using a ResNet-50 backbone for feature extraction.
## Features
• **End-to-End Object Detection:** From image input to output bounding boxes and class predictions.

• **ResNet-50 Backbone:** Pre-trained on ImageNet, the ResNet-50 backbone serves as a feature extractor.

• **Transformer Architecture:** Provides robust performance with fewer training iterations.

• **Compatibility:** Trained and tested on COCO dataset, adaptable for other datasets.

## Model Architecture
This implementation uses:

•	**ResNet-50:** Extracts features from the input image.

•	**Transformer Encoder-Decoder:** Processes the feature maps and outputs object queries corresponding to objects in the image.

•	**Feed-forward Network (FFN):** Predicts class labels and bounding boxes from the transformer’s output.
## Model description
The DETR model is an encoder-decoder transformer with a convolutional backbone. Two heads are added on top of the decoder outputs in order to perform object detection: a linear layer for the class labels and a MLP (multi-layer perceptron) for the bounding boxes. The model uses so-called object queries to detect objects in an image. Each object query looks for a particular object in the image. For COCO, the number of object queries is set to 100.

The model is trained using a "bipartite matching loss": one compares the predicted classes + bounding boxes of each of the N = 100 object queries to the ground truth annotations, padded up to the same length N (so if an image only contains 4 objects, 96 annotations will just have a "no object" as class and "no bounding box" as bounding box). The Hungarian matching algorithm is used to create an optimal one-to-one mapping between each of the N queries and each of the N annotations. Next, standard cross-entropy (for the classes) and a linear combination of the L1 and generalized IoU loss (for the bounding boxes) are used to optimize the parameters of the model.






## Screenshots

![App Screenshot](https://github.com/Surbhipatil/DETR-End-to-End-Object-Detection-/blob/main/Screenshot%202024-10-14%20182629.png)

## Training data
The DETR model was trained on COCO object detection, a dataset consisting of 118k/5k annotated images for training/validation respectively.
## Training procedure
**Preprocessing**

Images are resized/rescaled such that the shortest side is at least 800 pixels and the largest side at most 1333 pixels, and normalized across the RGB channels with the ImageNet mean (0.485, 0.456, 0.406) and standard deviation (0.229, 0.224, 0.225).

**Training**

The model was trained for 300 epochs on 16 V100 GPUs. This takes 3 days, with 4 images per GPU (hence a total batch size of 64).

**Evaluation results**

This model achieves an AP (average precision) of 42.0 on COCO 2017 validation. For more details regarding evaluation results, we refer to table 1 of the original paper.

## Output

![App Screenshot](https://github.com/Surbhipatil/DETR-End-to-End-Object-Detection-/blob/main/10_pactical_output.PNG)
