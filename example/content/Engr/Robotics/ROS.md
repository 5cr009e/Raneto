# ROS

## Create package with catkin

[Creating a catkin Package](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)

```bash
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```

Then run 

```bash
catkin build && source ~/catkin_ws/devel/setup.bash
```

## Using rospy

[Writing a Simple Publisher and Subscriber](http://wiki.ros.org/rospy_tutorials/Tutorials/WritingPublisherSubscriber)

Remember to 

```bash
chmod +x
```

otherwise the docker terminal will crash



## Driving the rc_car with ackermann model

```python
frame_id = 'base_link'
```

https://github.com/mit-racecar/racecar_gazebo/blob/master/racecar_control/scripts/keyboard_teleop.py

## Ackermann driving

[Planning for car-like robots]([http://wiki.ros.org/teb_local_planner/Tutorials/Planning%20for%20car-like%20robots](http://wiki.ros.org/teb_local_planner/Tutorials/Planning for car-like robots)), belongs to [teb_local_planner_tutorials](http://wiki.ros.org/action/fullsearch/teb_local_planner_tutorials?action=fullsearch&context=180&value=linkto%3A"teb_local_planner_tutorials")

