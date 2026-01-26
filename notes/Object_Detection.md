YOLO
1. The image is resized to (image_size, image_size) before input to the backbone. For example image_size=224 or 448 are commonly used (224 or 448 for Resnet backbone, that outputs  7x7 or 14x14 feature map). 
2. The TLWH box format from COCO is converted to $x_1y_1x_2y_2$ format and divided by (w,h,w,h).
3. The  box encoder purpose is to provide (image, target) pair for training. In box encoder the boxes in $x_1y_1x_2y_2$ format is converted to $x_cy_cwh$ format. The offset from the center of each bbox to the top-left corner of each grid cell which is $delta\_xy$ is computed by :
	1. For instance, if S=num_cell=7 (or 14), then cell_size = 1/7. 
	2. To convert to grid cell coordinate divide $x_cy_c$ by cell_size. To convert back to image coordinate multiply by $cell\_size$. 
	3. In grid cell coordinate, $ij=floor(cxcy\_sample/cell\_size)$, top-left corner (in image coordinate): $xy=ij*cell\_size$. The offset in grid cell coordinate is $delta\_xy=(cxcy\_sample-xy)/cell\_size$. Now, $delta\_xy$ is in the range \[0,1\] in grid cell coordinate and is to be regressed by the network. 
4. YOLO outputs a feature map tensor of size $(S,S,B*5+C)$. B is the number of candidate boxes. Note: there are no anchor boxes in YOLOv1.
5. why 5? because the box is of the format $[\delta_x, \delta_y, w, h, conf]$ plus C possible classes for the one box predicted per grid cell.
6. In YOLOv1 it is assumed that there is only one true box per grid cell. Therefore, to match the size of the output tensor (for computing loss). In the third axis of size $B*5+C$ only one ground truth box is used and is repeated B consecutive times throughout the third axis. 
7. To recover $x_1y_1x_2y_2$ format to compute IOU, because width and height of box is always in image coordinate it does not need to be multiplied by $cell\_size$: 
	1. $box\_xyxy[:,:2]=box1[:, :2]*cell\_size - 0.5*box1[:,2:4]$
	2. $box\_xyxy[:,2:4]=box1[:, :2]*cell\_size + 0.5*box1[:,2:4]$
	3. This is done so because when combining the two information they should share the same coordinate scale.
	4. Note: normally a function to compute IOU expects $x_1y_1x_2y_2$ format.
8. Box width and height are regressed directly as after normalization by image_size they are in the range\[0,1\] in image coordinates.
9. During training, bounding box assignment is done to assign one candidate ground truth box (since there are B copies of the same ground truth box) to B prediction boxes in each grid cell based on their IOUs. Note: not all B predicted boxes may ever get to be assigned during training. Note: This part is replaced with Hungarian algorithm in DETR, which is used during training only.
10. The last activation function in the model is a Sigmoid function. 
11. YOLO treats object detection as a regression problem. The loss function is in the form:
12. $L = L_{Localisation} + \lambda_{coobj}*L_{coobj} + \lambda_{noobj}*(L_{noobj}+L_{coo\_no\_response}) + L_{classification}$
13. What I learned from implementing YOLOv1 from scratch:
	1. Training to improve mAP is tough. After 100 epochs the model only achieved ~2% mAP on the CODA dataset.
	2. The idea of using anchor boxes becomes obvious.
	3. Ways to improve mAP include hyperparameter tuning such as grid search using wandb sweeps.  