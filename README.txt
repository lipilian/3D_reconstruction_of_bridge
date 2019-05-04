# github: lipilian 
#LiuHong_Camera_index_R_T format:
<num_cameras> <num_points> [two integers]
<camera1>
<camera2>
   ...
<cameraN>

*****=================================*****************
Camera geometry have the following format:
<f> <k1> <k2>  [the focal length, followed by two radial distortion coefficients]
<R>            [a 3x3 matrix representing the camera rotation]
<t>            [a 3-vector describing the camera translation]


*****=================================*****************

# LiuHong_Point_Collect format:
<point1>
<point2>
  ...
<pointM>

*****=================================*****************
Each point entry has the form:

<position> [a 3-vector describing the 3D position of the point]
<color>   [a 3-vector describing the RGB color of the point] I think it is RGB instead of BGR ^_^
<view list> [a list of views the point is visible in]

*****=================================******************

<view list> begin with the length of the list(i.e the number of cameras the point is visible in).
The list is then given as a list of quadruplets <camera> <key> <x> <y>, where <camera> is a camera index,
<key> is the index of the sift keypoint where the point was detected in that camera (for this project, we
are not going to use this parameter), and <x>, <y> are the detected positions of that keypoint. Both indices are 
0-based.

****important: The pixel positions are floating point numbers in a coordinate system where the origin is the
center of the image, the x-axis increase to the right, and the y-axis increases towards the top of the image.
Thus, (-w/2,-h/2) is the lower-left corner of the image, and (w/2,h/2) is the top-right corner (where w and h
are the width and height of the image)
