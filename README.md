# f110-skeletons-spring2019
Skeleton codes for F110 Spring 2019 course at Oregon State University.

In order to add the contents of this repository to your workspace on your local machine, do the following:

Clone this repository into a folder on your computer. `--recurse-submodules` is important as it will pull the cartographer submodules needed for SLAM.
```bash
$ cd ~/sandbox (or whatever folder you want to work in)
$ git clone --recurse-submodules https://github.com/sabotagelab/f110-skeletons-spring2019.git
```
This repository exists as a catkin workspace. 

If you are on Ubuntu 16.04/ROS Kinetic, you will need to update your proto compiler to proto3. Beware: This can cause issues if you are working on other projects involving Gazebo (such as building custom Gazebo plugins). For this class it should not cause any issues, and if you are Ubuntu 18.04 or newer you can skip this step:
```bash
$ src/cartographer/scripts/install_proto3.sh
```

You will need to install ros depencies. You should be able to do this through the following while inside the repository:
```bash
$ sudo rosdep init
$ rosdep update
$ rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
```

Make all the Python scripts executable (by default they are set to non-executable when downloaded from Github, or anywhere for that matter)
```bash
find . -name "*.py" -exec chmod +x {} \;
```

Additionally, the `python-catkin-tools` build chain is reccomended for working with ROS. After installing that with git, you can build the workspace using
```bash
$ catkin build
```

The generated devel and build folders at the root of the workspace are where the linked libraries and the compiled code in machine language resides. Source the environment using
```bash
$ source devel/setup.bash
```

You can now run a launch file using the following. 
```bash
$ roslaunch gap_finding gap_finding_sim.launch
```

TROUBLESHOOTING
If for some reason you get a build error, try deleting the CMakeLists.txt file and running `catkin build` again. 
