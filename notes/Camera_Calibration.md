1. The extrinsic camera parameter aka. camera pose is not constant unless the camera is placed fixed to a world coordinate frame.
2. PnP is used to get the transformation from world to camera given the point correspondences of 3D-2D. Or more formally:
3. Camera pose estimation: Given a set of 3D points wrt. a world coordinate system and their projecting points in the image plane, compute the rigid transformation between the world and the camera coordinate systems. 
4. For perspective imaging device, this is the so-called *perspective n point (PnP)* problem.
5. PnP problem: n 3D-2D correspondences (i.e. correspondences between 3D model points and image points) $\rightarrow$ Find Rotation and Translation $(R, T)$.
6. EPnP: An accurate $O(n)$ solution to the PnP problem.

References: 
1. Barycentric coordinate system https://en.wikipedia.org/wiki/Barycentric_coordinate_system
2. Vincent Lepetit · Francesc Moreno-Noguer · Pascal Fua, "EPnP: An Accurate O(n) Solution to the PnP Problem", International Journal of Computer Vision ,February 2009