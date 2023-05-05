# Template for ros foxy docker environment for vscode

Environment build with usage of instruction on ros [humble website](https://docs.ros.org/en/humble/How-To-Guides/Setup-ROS-2-with-VSCode-and-Docker-Container.html)

## Requirements
- Visual Studio Code
  - Remote Development Extension
- Docker

## Usage
You can use setup by changing to one of the exisiting branches such as:
- humble: ROS2 humble
- foxy: ROS2 foxy
- master: ROS2 foxy

After cloning repository into your ros workspace checkout branch with `ROS_DISTRO` you want to use and then go into src directory and then launch vscode. 
<!-- By default docker is being created via root but if you want to change it edit both of the files in `.devcontainer` directory to contain proper `USERNAME` instead of USERNAME.  -->
Then change all the necessary instances of `USERNAME` word in `devcontainer.json` file and afterwards one instance in arguments of `Dockerfile`.
If Editing `ROS_DISTRO` remember to edit both of the files as you have done with `USERNAME`. Change all of the necessary `foxy` strings to any distro you want and do the same to packages you install in Dockerfile. If necessary use `Ctrl+Shift+P` and then lanuch `Dev Containers: Rebuild and Reopen in Container`. This operation will start building docker foxy(which is pulled by default in Dockerfile). After this process of setting up environment should be ready.

## Test setup
You can test if everything works fine with commands as following:
```bash
sudo apt install ros-$ROS_DISTRO-rviz2 -y
source /opt/ros/$ROS_DISTRO/setup.bash
rviz2
```

## Nvidia support
If user wants to use nvidia container toolbox inside of the container they can uncomment run args in src/.devcontainer/devcontainer.json

# Usefull information
- To start container go to `src` directory and launch `Visual Studio Code` in there. Afterwards use `Dev Containers: Rebuild and Reopen in Container`
- If build is failing check `devcontainer.json` and `Dockerfile` contents, especially usage of USERNAME variables. If something else is failing check build log
- If ros build is failing or some packages cannot be detected you can update ROS packages via using command:
```bash
rosdep update
```