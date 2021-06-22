 # task1-ROS-installation-and-configuration

### after do this step to install ROS melodic in ubuntu : 
* download virtualbox 
* install ubuntu
* install ROS " melodic version " 


#### we will now preparing a ROS by create a ROS workspace : 
( hint : A catkin workspace is a folder where you modify, build, and install catkin packages. )
<p><code>$ mkdir -p ~/catkin_ws/src</code></p>
<p><code>$ cd ~/catkin_ws/</code></p>
<p><code>$ catkin_make</code></p>

![task1backupforcatkin](https://user-images.githubusercontent.com/56357074/122817274-6097cb00-d2e0-11eb-8f71-b7657a86be21.png)

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

#### then enter to the file that is called  bashrc , this file is a script file that's executed when a user logs in.

<p><code>$ sudo nano ~/.bashrc</code></p>

##### and write this line at the end of this file :

<p><code>source /home/rmsh/catkin_ws/devel/setup.bash</code></p>

##### and save change 

## to controling the motors of robot arm by Rviz : 

<p><code>$ roslaunch robot_arm_pkg check_motors.launch</code></p>

![task1p2](https://user-images.githubusercontent.com/56357074/122844100-90a79400-d309-11eb-870e-e1602bef5256.png)

## to use Arduino with ROS :

* install Arduino IDE :
  -  go to [install Arduino IDE](https://www.arduino.cc/en/software) , after install Arduino IDE ,extraction and run `install.sh` file on terminal to make a shortcut of arduino in dsktop
  -  install rosserial by 2 commands: 
     - <p><code>$ sudo apt-get install ros-melodic-rosserial</code></p>
     - <p><code>$ sudo apt-get install ros-melodic<distro>-rosserial-arduino</code></p>
  - all previous steps is to install a nessessary packages
  - install a ros_lib which is the package that arduino need to allow arduino to interact with ROS :
    - you can do this step by go to arduino window and do this from setting but i make this step by commands .
    - <p><code>$ cd arduino<sketchbook>/libraries</code></p>
    -  ` <sketchbook> ` is a directory that the linux arduino enviroment saves your sketches .
    - hint: you have to delete ros_lib if there are to regenerate , because if there is , that's may cause errors:
         <p><code>$ rm -rf ros_lib</code></p>
    - then create now a `ros_lib` directory by this command :
         <p><code>$ rosrun rosserial_arduino make_libraries.py</code></p>
 * identify a USB to arduino : 
      #### devices > USB > and select a USB
 * upload arduino code :
   - select Arduino port
   - change permission:
     <p><code>	$ ls -l /dev |grep ttyUSB</code></p>
     <p><code>	$ sudo chmod -R 777 /dev/ttyUSB0</code></p>
   - upload the code from Arduino IDE



