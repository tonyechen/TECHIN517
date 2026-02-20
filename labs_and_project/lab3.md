# Lab 3: I like to MoveIt MoveIt


## Learning Objectives

- Setup a robot manipulator using MoveIt
- Control the SO101 arm using forward kinematics
- Control the SO101 arm using inverse kinematics


## TODO

1. Create a MoveIt configuration package for the robot arm:  
    1. Run the following command to bringup the MoveIt Setup Assistant:  
        ```bash
        ros2 launch moveit_setup_assistant setup_assistant.launch.py
        ```
    2. On the start screen, choose "Create New MoveIt Configuration Package"  
        Set the URDF file to: `/home/ubuntu/techin517/so101_ws/src/soa_ros2/soa_description/urdf/soa.urdf`  
    3. On the Self-Collisions page, press "Generate Collision Matrix"  
    4. On the Virtual Joints page, select "Add Virtual Joint"  
        Name it `virtual_joint`  
        Set the Child Link to `base_link`  
        Set the Parent Link to `world`  
        Make sure it's a `fixed` joint
    5. On the Planning Groups page, select "Add Group"  
        Set "Group Name" to `arm`  
        Set "Kinematic Solver" to `kdl_kinematics_plugin/KDLKinematicsPlugin`  
        Set "Kin. Search Timeout (sec)" to `1.0`  
        Set "Group Default Planner" to `RRTConnect`  
        Press "Add Joints" and add: 
        - `base_joint`
        - `shoulder_pan`
        - `shoulder_lift`
        - `elbow_flex`
        - `wrist_flex`
        - `wrist_roll`

        Press "Add Group" again  
        Set "Group Name" to `gripper`  
        Press "Add Joints", add the `gripper`  
        Save
    6. On the Robot Poses page, select "Add Pose"  
        Set "Pose Name" to `open`  
        Set "Planning Group" to `gripper`  
        Slide the position all the way open  
        Save and select "Add Pose" again  
        Set "Pose Name" to `closed`  
        Set "Planning Group" to `gripper`
        Slide the position all the way closed  
        Save  
    7. On the End Effectors page, select "Add End Effector"  
        Set "End Effector Name" to `end_effector`  
        Set "End Effector Group" to `gripper`  
        Set "Parent Link" to `gripper_link`  
        Set "Parent Group" to `arm`  
        Save  
    8. On the ROS2 Controllers page, select: "Auto Add JointTrajectoryController Controllers For Each Planning Group"  
        Click on the gripper controller and select "Edit Selected"  
        Change the controller type to `position_controllers/GripperActionController`
    9. On the MoveIt Controllers page, select: "Auto Add FollowJointsTrajectory Controllers For Each Planning Group"  
        Click on the gripper controller and select "Edit Selected"  
        Change the controller type to `GripperCommand`
    10. On the Author Information page, enter your name and school email
    11. On the Configuration Files page, select "Browse"  
        Navigate to the `src/soa_ros2/` folder of your workspace  
        Create a folder called `soa_moveit_config`  
        Click "choose"  
        Click "Generate Package"  
    12. Click "Exit Setup Assistant"  
    13. In the newly created package, open the file `soa_moveit_config/config/joint_limits.yaml`  
        Change all integers to floats: e.g. `10` >> `10.0`
    14. In `soa_moveit_config/config/kinematics.yaml` set any integers to floats
    15. Build your workspace  
    16. Make sure it worked by running
        ```bash
        # TODO
        ```

2. Fill in the example code to pick up a block using forward kinematics.

3. Fill in the example code to pick up a block using inverse kinematics.


## Deliverables


## FAQ


## Resources
