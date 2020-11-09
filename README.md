# robot-ball-chaser-loc
## Summary
Application running on ros and gazebo for a mobile robot equipped with a laser scanner and RGBD camera, mapping a given indoor environment using the Graph SLAM package, RTAB-Map.    
## Implementation
1. Gazebo world models an indoor enviornment and spawns a differential drive robot equipped with a 2D LIDAR and RGBD camera. 
2. As the robot navigates through the environment (keyboard teleop), RTAB-Map creates and manages nodes and constraints based on environmental sensing and odometry.
3. Finally, RTAB-Map iterates for an optimal solution to the graph constraints, yielding the most probable robot pose and map combination.

## Usage
1. Launch the gazebo world, keyboard teleop and mapping application using:
<code> roslaunch my_robot world.launch </code>
<code> rosrun teleop_twist_keyboard teleop_twist_keyboard.py </code>
<code> roslaunch my_robot amcl.launch </code>
2. Verify that the initial pose of the robot is correct, and specify a goal poition on RViz. 
## Sample database
https://drive.google.com/file/d/1bPP1X1Cie6FZdJNz_8ChCedKvi4QiPqX/view



