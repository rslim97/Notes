## 2D ###
1. In computer vision pixelwise dense prediction is the task of predicting a label for each pixel in the image [https://arxiv.org/abs/1611.09288](https://arxiv.org/abs/1611.09288).
	1. Semantic segmentation: classify per pixel
	2. Depth estimation: regress per pixel.
	3. Instance segmentation: classify per pixel per object.
	4. Panoptic segmentation: handles both stuff (semantic segmentation) and things (instance segmentation).
		1. Assign (category, instance_id) pair to each pixel in image.
		2. Instance label ignored for "stuff" categories.
2. Mask R-CNN for instance segmentation
	1. Boxes first paradigm:
		1. Run detector (Faster-RCNN).
		2. Produce segmentation relative to each predicted box.
	2. Mask R-CNN combines both steps into an end-to-end trainable model.
3. Dense Prediction Transformer
### 3D ###
1. semantic segmentation: 
	1. Point cloud: PointNet
	2. Voxel: 3D U-Net
2. instance segmentation: SoftGroup

References:
1. CSEP 576: Dense prediction, Udub, Jonathan Huang, 2020.