 # task1-ROS-installation-and-configuration

#### after do this step to install ROS melodic in ubuntu : 
* download virtualbox 
* install ubuntu
* install ROS " melodic version " 


#### we will now preparing a ROS by create a ROS workspace : 
( hint : A catkin workspace is a folder where you modify, build, and install catkin packages. )
<p><code>$ mkdir -p ~/catkin_ws/src</code></p>
<p><code>$ cd ~/catkin_ws/</code></p>
<p><code>$ catkin_make</code></p>

#### any change in a ROS enviroment its conveinent to be added automatically to your bash session  every time a new shell is launched :

<p><code>$ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc</code></p>
<p><code>$ source ~/.bashrc</code></p>

## installing the package of arduino_robot_arm 

####  go to src folder which is in catkin_ws and add a package of arduino_robot_arm :

<p><code>$ cd ~/catkin_ws/src</code></p>
<p><code>$ sudo apt install git</code></p>
<p><code>$ git clone https://github.com/smart-methods/arduino_robot_arm</code></p>

#### after that go to catkin_ws and install all dependencies :

<p><code>$ cd ~/catkin_ws</code></p>
<p><code>$ rosdep install --from-paths src --ignore-src -r -y</code></p>
<p><code>$ sudo apt-get install ros-melodic-moveit</code></p>
<p><code>$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui</code></p>
<p><code>$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher</code></p>
<p><code>$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control</code></p>

#### after that compile the package by :

<p><code>$ catkin_make</code></p>


