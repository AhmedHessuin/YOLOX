# YOLOX

# Paper Discussion

## What do you like about it?
- i like how they changed the idea of anchors to anchorless and using the decoupled heads
- i like how they looked about the types of augmentations to use and what to drop, and how they explained that the augmentations vary between deep and shallow models 
- i like how they make clear explanation about the modification for decouple and the metric presentation 
- i like how they started with yolov3 because yolov4 and yolov5 over-optimized for the anchor based pipline, so to get better result as experiment better test with weak or bad model to see what is the gain from your experiments 
- i like how the training settings are mostly consistent from the baseline to our final model 
- i like the idea of adding Classification augmentation (MixUp) in object detection task, even if it was for the last 15 epoch 
- i like how they stated the effect of anchor hyperparmeters issue, like clustering and it's domain specific, and how it's hard if we will moving such large amount of predictions between devices (e.g., from NPU to CPU) may become a potential bottleneck in terms of the overall latency. 
- i like the work around OTA to make simOTA
## what do you dislike about it ?
- i didn't like the poor build of the repo, like no tutorial colab, like the YOLO repos 
## what are the main contributions?
- adding a decoupled head 
![](https://snipboard.io/O7mt0o.jpg)
- Anchor free 
- using IOU loss and IoU-aware branch.
- using BCE Loss for training cls and obj branch,and IoU Loss for training reg branch.
- Augmentation Selection (conduct RandomHorizontalFlip,ColorJitter and multi-scale for data augmentation and discard the RandomResizedCrop strategy)
- NMS free end-to-end yolo
- MixUp augmentation added 
- Multi positives for the anchor free 
- SimOTA Advanced label assignment is another important progress of object detection
- Strong augmentation ( MixUp and Mosaic)
## How do they differ from previous YOLO models?
- Anchor free 
- Decoupled Head 
- SimOTA
- Strong augmentation (MixUp)
## What do you think are potential areas of improvement?
- Model Backbone 
- Transformer modules
# Test 
can be found in [tahaulf.ipynb](tahaulf.ipynb)
the reported result in the .ipynb is 
```
Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.469
```
same as [standard model YOLOX-m](https://github.com/Megvii-BaseDetection/YOLOX#standard-models)
