
## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

## Training data
The DETR model was trained on COCO object detection, a dataset consisting of 118k/5k annotated images for training/validation respectively.
## Training procedure
**Preprocessing**

Images are resized/rescaled such that the shortest side is at least 800 pixels and the largest side at most 1333 pixels, and normalized across the RGB channels with the ImageNet mean (0.485, 0.456, 0.406) and standard deviation (0.229, 0.224, 0.225).

**Training**

The model was trained for 300 epochs on 16 V100 GPUs. This takes 3 days, with 4 images per GPU (hence a total batch size of 64).

**Evaluation results**

This model achieves an AP (average precision) of 42.0 on COCO 2017 validation. For more details regarding evaluation results, we refer to table 1 of the original paper.

## output

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

