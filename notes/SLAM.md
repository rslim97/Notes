### 2D ###
1. Hector SLAM
	1. Hector's overall algorithm is very direct, the laser point is "aligned" with the existing map
	2. Three important parts:
		1. Bilinear interpolation.
		2. Scan-matching using Gauss-Newton.
		3. multi-resolutions maps: coarse to fine strategy. Instead of using multi resolution map, it maintain the occupancy grid maps on all resolutions. Scan matching is performed at the coarsest level and the pose from the coarser level is used as initial estimate for matching in finer resolution. After obtaining the pose estimate from the finest resolution, the scan is inserted into the occupancy map at all levels.
	Weakness:
	3. Only SLAM frontend, no loop closure mechanism.
	4. Relies only on range data, information coming from odometry is not used at all. 
	5. Although it is mentioned that the system provides 6-DOF pose estimate, the one implemented in ROS provides only 3-DOF pose estimate. The 3D state estimation is not implemented.
	6. For the dual linear difference in bilinear interpolation, there is theoretically a possibility of discontinuit, and Pm may run out of square surrounded by P00->P11 during iteration during the calculation. This problem has been improved by google's cartographer to a three linear difference.
	7. There is no ability to modify the map, once the map is wrong, the subsequent matching also appear problems.
	
	
	References:
	8. S. Kohlbrecher, O. Von Stryk, J. Meyer, and U. Klingauf, “A flexible and scalable SLAM system with full 3D motion estimation,” 9th IEEE International Symposium on Safety, Security, and Rescue Robotics, SSRR 2011, pp. 155–160, 2011.
	9. A Review of 2D SLAM Algorithms on ROS, Bayu Kanugrahan Luknanto. Polimi. 2018-2019.
	
2. Gmapping
	References:
	1. G. Grisetti, C. Stachniss, and W. Burgard, “Improved techniques for grid mapping with Rao-Blackwellized particle filters,” IEEE Transactions on Robotics, vol. 23, no. 1, pp. 34–46, 2007

3. google cartographer

	References:
	1. W. Hess, D. Kohler, H. Rapp, and D. Andor, “Real-time loop closure in 2d lidar slam,” in Robotics and Automation (ICRA), 2016 IEEE International Conference on. IEEE, 2016, pp. 1271–1278.
