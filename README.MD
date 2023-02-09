# Turtlebot3 Mesh navigation

This package is a working simulation of [mesh navigation](https://github.com/uos/mesh_navigation) which uses [move_base_flex](https://github.com/magazino/move_base_flex) for turtlebot3.

## Map and files in this repo

The map is from the [repo of the pluto robot](https://github.com/uos/pluto_robot) and most of the files in this repo are from one of those four repos :

- [pluto robot](https://github.com/uos/pluto_robot) : the maps and the mesh_navigation yaml config
- [mesh navigation](https://github.com/uos/mesh_navigation)
- [move_base_flex](https://github.com/magazino/move_base_flex)
- [turtlebot3_mbf](https://github.com/Rayman/turtlebot3_mbf) : the idea and the launch file for the simulation

## Installation

git-lfs: `sudo apt install git-lfs`

Turtlebot simulation: `sudo apt install ros-noetic-turtlebot3-gazebo ros-noetic-turtlebot3-navigation`

move_base_flex: `sudo apt install ros-noetic-move-base-flex`

mesh_navigation: `sudo apt install ros-noetic-mesh-navigation ros-noetic-rviz-map-plugin`

It uses git lfs to store binary files.

## Simulation

Start simulation: `TURTLEBOT3_MODEL=burger roslaunch turtlebot3_mesh_nav sim.launch`

Start mesh nav server: `roslaunch turtlebot3_mesh_nav move_base_flex.launch`

To start the navigation you should publish on topic `/move_base_flex/move_base/goal` _(for some reason the topic used on the pluto robot repo is `/move_base_flex/get_path/goal` which only generates the global path but doesn't actually transfer the result to the local planner. Please read the [move_base_action.cpp of move_base_flex](https://github.com/magazino/move_base_flex/blob/master/mbf_abstract_nav/src/move_base_action.cpp) to understand how the informations are transfered in the navigation stack)_

Also, you can simply do: `roslaunch turtlebot3_mesh_nav start_experiment.launch`. _Be aware that the turtlebot will slip on the terrain for this path_.

</br>
</br>
</br>

Assembled by Sébastien K. for CoHoMa 2023 - U2IS Team.
