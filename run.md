1. YOLO Object Detection Demo
This will use the front camera to detect objects in the simulation.

Terminal 1: Start the simulator (I suggest spawning at 0,0 so you can see things easily):

bash
```
python3 launch_gem.py --x 12.5 --y -21 --yaw 3.1416
```
Terminal 2: Open a new terminal, enter the container, and launch the detector:

bash
```
distrobox enter noetic-sim -- bash -c "source /opt/ros/noetic/setup.bash && source /hdd/kevin/noetic_home/gem_simulation_ws/devel/setup.bash2 && roslaunch gem_gazebo yolo_detector.launch"
```


2. DWA Path Planning Demo
This makes the car plan a path to a goal coordinate.

Terminal 1: Start the simulator as usual.
Terminal 2: Launch the DWA planner:
bash
```
distrobox enter noetic-sim -- bash -c "source /opt/ros/noetic/setup.bash && source /hdd/kevin/noetic_home/gem_simulation_ws/devel/setup.bash && roslaunch gem_dwa_sim dwa_sim.launch goal.x:=-20.0 goal.y:=-20.0 yaml_path:=\$(rospack find gem_gazebo)/scenes/highbay_track.yaml"
```

3. Pure Pursuit / Stanley (Auto-Steering) Demos
These are for the older e2 model on a test track.

Terminal 1:
bash
```
distrobox enter noetic-sim -- bash -c "source /opt/ros/noetic/setup.bash && source /hdd/kevin/noetic_home/gem_simulation_ws/devel/setup.bash && roslaunch gem_launch gem_init.launch world_name:='track1.world' vehicle_name:=e2"
```

Terminal 2:
bash
```
distrobox enter noetic-sim -- bash -c "source /opt/ros/noetic/setup.bash && source /hdd/kevin/noetic_home/gem_simulation_ws/devel/setup.bash && rosrun gem_pure_pursuit_sim pure_pursuit_sim.py"
```

Pro Tip: If you want to manually drive the car around with your keyboard to test things, the README mentions you can use:

bash
```
python3 /hdd/kevin/noetic_home/gem_simulation_ws/src/POLARIS_GEM_Simulator/utils/generate_waypoints.py
```