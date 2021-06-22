 # task1-ROS installation and configuration

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


![task1p4](https://user-images.githubusercontent.com/56357074/122844631-be410d00-d30a-11eb-8ea0-d68c0c432193.png)

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

     
## controling the motors in simulation : 
   * run a Rviz : 
          <p><code>	$ roslaunch robot_arm_pkg check_motors.launch</code></p>

![task1p6](https://user-images.githubusercontent.com/56357074/122854091-df5e2980-d31b-11eb-8205-5b2a09fda15b.png)



   * run a gazebo :
             <p><code>	$ roslaunch robot_arm_pkg check_motors_gazebo.launch</code></p>
     
     ![task1p7](https://user-images.githubusercontent.com/56357074/122854125-e8e79180-d31b-11eb-8cdd-34d4418a5ce2.png)

   * because gazebo seperate from Rviz , use this command to you can control a robot arm from joint state publisher and will simulate in gazebo : 
                  <p><code>$ rosrun robot_arm_pkg joint_states_to_gazebo.py</code></p>
   * ( hint : you may need to change permission):
                  <p><code>$ 	$ cd catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts</code></p>
                  <p><code>$ 	$ sudo chmod +x joint_states_to_gazebo.py</code></p>
     
     https://user-images.githubusercontent.com/56357074/122854373-509ddc80-d31c-11eb-8901-4046c96489d3.mp4

## controlling robot arm by moveit : 
     
   * to run a moveIt , you need first Launch the setup assistant:
                  <p><code>$ roslaunch moveit_setup_assistant setup_assistant.launch</code></p>
     
     
![task1p9](https://user-images.githubusercontent.com/56357074/122854624-aa060b80-d31c-11eb-906a-128118f33dfd.png)

   * and choose `create new ...` and select the path of arduino .urdf  and the load files 
   * to run moveit in Rviz :
                  <p><code>$ roslaunch moveit_pkg demo.launch</code></p>
     ![task1p10](https://user-images.githubusercontent.com/56357074/122854649-b4280a00-d31c-11eb-85b2-d91044461494.png)


   * go to `Add` button and select `motion planning`
   * to run a gazebo with moveit which is in Rviz to simulation : 
                  <p><code>$$ roslaunch moveit_pkg demo_gazebo.launch</code></p>
     
     
     ![task1p11](https://user-images.githubusercontent.com/56357074/122854675-bbe7ae80-d31c-11eb-8e36-a48f70c69574.png)

 
    
     

