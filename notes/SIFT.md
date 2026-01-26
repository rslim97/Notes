
1. People say 'SIFT' but there are two parts to SIFT [1]. 
		1. an interest point detector.
		2. a region descriptor.
	1. They are independent, many people use the region descriptor without looking for the points.
2. SIFT summary[2]:
	1. Extract a 16x16 patch around detected keypoint.
	2. Compute the gradients and apply a Gaussian weighting function.
	3. Divide the window into a 4x4 grid of cells.
	4. Compute gradient direction histograms over 8 directions in each cell.
	5. Concatenate the histograms over 8 directions in each cell.
	6. Concatenate the histograms to obtain 128 dimensional feature vector.
	7. Normalize to unit length.

![[Screenshot 2026-01-21 150833.png]]

Local features: main components [3]
1. Detection: Identify the interest points.
2. Description: Extract vector feature descriptor surrounding each interest point.
3. Matching: Determine correspondence between descriptors in two views.


References:
1. CSE576 Udub Linda Shapiro
2. Trym Vegard Haavardsholm, UNIK4690
3. CSIE5429 3D-DLCV, Spring 2021
