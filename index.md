# robot-ball-chaser
## Summary
Application running on ros and gazebo for a mobile robot chasing a white ball in its field of view in a given indoor enviornment. Uses RGB camera to detect the ball's approximate location within its field of view, assuming the ball is the only white object in the robot's surrounding. 
## Video 
<figure class="video_container">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/SufdCHqg5-w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</figure>

## Implementation
1. Gazebo world models an indoor enviornment with a white ball and spawns a differential drive robot equipped with a LIDAR and RGB camera. 
2. The camera's field of view is scanned for white pixels, and the robot is driven left, straight or right depending on the location of the first white pixel detected in the image. 
2. Low-level control of the mobile robot is achieved through a Gazebo plugin for differential drives. 
## Usage
1. Place the ball_chaser and my_robot folders within an src folder in your project directory. 
2. Run <code> catkin_make </code> in the project directory to make this your catkin workspace.
3. After the packages have compiled separately, setup the environment variables by running <code> source devel/setup.bash </code> and launch the gazebo world and the ball_chaser application using:
<code> roslaunch my_robot world.launch </code>
<code> roslaunch ball_chaser ball_chaser.launch </code>
4. To visualize the robot's camera stream, launch <code> rqt_image_view </code> and visualize the topic /camera/rgb_camera/image_raw.
5. Move the ball within the robot's field of view and verify that the robot moves to track the ball location within its field of view.
## Improvements
1. The first white pixel in the image is used to estimate the approximate location of the ball. For better tracking of the ball, one can apply a color filter on the image and then detect a circular contour, and drive the robot towards the center of this contour.
2. Allowing other white objects in the background and discerning the ball from them.
