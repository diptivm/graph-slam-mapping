# robot-ball-chaser-loc
## Summary
Application running on ros and gazebo for a mobile robot localizing in a given indoor environment and navigating autonomously to an input goal position. Assumes fixed map and initial pose.  
![Localization screenshot](https://github.com/diptivm/robot-ball-chaser-loc/blob/gh-pages/Localization_screenshot.png?raw=true)
## Implementation
1. Gazebo world models an indoor enviornment and spawns a differential drive robot equipped with a 2D LIDAR and RGB camera. 
2. The ROS map_server publishes a 2D map of the environment, created in advance using the pgm-map-creator package. 
3. The LIDAR scan data is used for localization based on the adaptive Monte-Carlo localization method (AMCL), implemented in the ROS amcl node.
4. The ROS move_base node is invoked for path planning to the specified goal location.
## Usage
1. Launch the gazebo world and the localization/ navigation application using:
<code> roslaunch my_robot world.launch </code>
<code> roslaunch my_robot amcl.launch </code>
2. Verify that the initial pose of the robot is correct, and specify a goal poition on RViz. 
## Improvements
The localization/ navigation application can be further tuned for the given indoor environment by experimenting with parameters of the amcl and move_base nodes. 
Some parameters that have been experimented with:
### AMCL node
1. odom_alpha_1-4: These quantify the noise in the odometry measurements and in this case have been reduced to allow greater trust in the odomotery readings. 
2. laser_max_beams: was initially increased to allow better localization, but was subsequently returned to its default value as no significant improvement was observed.
### Move_base node
1. pdist_scale: this quantifies the weighting for how close the robot should stay to the (globally planned) path it was given, and as reduced due to the small size of this room (and hence, preference to not deviate too much towards the walls). 
2. gdist_scale: given that pdist_scale was reduced, this was left at the default value, as increasing it made it difficult to recover from a stuck position.


