# ROS-VM-Connection

1. Activate SSH in both machine
systemctl status ssh
sudo apt-get install openssh-server
sudo systemctl enable ssh --now

2. Test the SSH connection between two machine
check the with ifconfig in terminal
![alt text](https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png)
ssh irfanrah@223.195.39.11
ssh ubuntu18@192.168.56.101

https://forums.virtualbox.org/viewtopic.php?t=85464
Don't use NAT network, use Host-only adapter


After this step, you must be able to access both machine

3. Clone this repo in both machine
cd catkin_ws/src
git clone https://github.com/irfanrah/ROS-VM-Connection

4. Multiple machine setup
http://wiki.ros.org/ROS/Tutorials/MultipleMachines

a. In master machine 
nano ~/.bashrc
export ROS_MASTER_URI=223.195.39.11:11311
export ROS_HOSTNAME=223.195.39.11

a. In slave machine
export ROS_MASTER_URI=223.195.39.11:11311
export ROS_HOSTNAME=10.0.2.15
