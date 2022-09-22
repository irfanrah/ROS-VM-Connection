# ROS-VM-Connection

1. You need to change the network on Virtual Machine, because NAT network (default) is not compatible with ROS communication
(http://wiki.ros.org/win_ros/Tutorials/WinRos%20and%20Virtual%20Ubuntu)
go to File > Host Network Manager > and set up a new profile like this

![alt text](https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/3.png)
After that, you can change the VM slave connection to Host-only Adapter
![alt text](https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png)

2. Check your ip with ifconfig in terminal
![alt text](https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/2.png)


3. Setup VM slave localhost with 
sudo nano /etc/hosts
add your ip and name on there
don't forget to close the terminal and reopen again

4. Activate SSH in both machine
systemctl status ssh
sudo apt-get install openssh-server
sudo systemctl enable ssh --now


2. Test the SSH connection between two machine
![alt text](https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png)
ssh irfanrah@192.168.56.1
ssh ubuntu18@192.168.56.101
if it's working and able to access both machine, you can proceed to the next step


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
