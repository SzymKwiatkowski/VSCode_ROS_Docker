# Template for ros foxy docker environment for vscode

Environment build with usage of instruction on ros [humble website](https://docs.ros.org/en/humble/How-To-Guides/Setup-ROS-2-with-VSCode-and-Docker-Container.html)

## Requirements
- Visual Studio Code
  - Remote Development Extension
- Docker

## Usage
After cloning repository into your ros workspace go into src directory and then launch vscode. Edit both of the files in `.devcontainer` directory to contain proper `USERNAME`. If Editing `ROS_DISTRO` remember to edit both of the files as you have done with `USERNAME`. Change all of the necessary `foxy` strings to any distro you want and do the same to packages you install in Dockerfile. If necessary use `Ctrl+Shift+P` and then lanuch `Dev Containers: Rebuild and Reopen in Container`. This operation will start building docker foxy(which is pulled by default in Dockerfile). After this process of setting up environment should be ready.

## Test setup
You can test if everything works fine with commands as following:
```bash
sudo apt install ros-$ROS_DISTRO-rviz2 -y
source /opt/ros/$ROS_DISTRO/setup.bash
rviz2
```