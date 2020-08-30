# robot-ball-chaser
## Summary
Application running on ros and gazebo for a mobile robot chasing a white ball in its field of view in a given indoor enviornment. Uses RGB camera to detect the ball's approximate location within its field of view, assuming the ball is the only white object in the robot's surrounding. 
## Implementation
1. Gazebo world models an indoor enviornment with a white ball and spawns a differential drive robot equipped with a LIDAR and RGB camera. 
2. The camera's field of view is scanned for white pixels, and the robot is driven left, straight or right depending on the location of the first white pixel detected in the image. 
2. Low-level control of the mobile robot is achieved through a Gazebo plugin for differential drives. 
## Usage
 
## Improvements
1. The first white pixel in the image is used to estimate the approximate location of the ball. For better tracking of the ball, one can apply a color filter on the image and then detect a circular contour, and drive the robot towards the center of this contour.
2. Allowing other white objects in the background and discerning the ball from them.
