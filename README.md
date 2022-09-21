# ROS-VM-Connection

1. Activate SSH in both machine
systemctl status ssh
sudo apt-get install openssh-server
sudo systemctl enable ssh --now

2. Test the SSH connection between two machine
check the with ifconfig in terminal
![alt text](https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png)
ssh irfanrah@223.195.39.11
ssh ssh ubuntu18@10.0.2.15
https://www.mathworks.com/matlabcentral/answers/392422-cannot-connect-to-ros-master-running-on-virtual-machine
https://www.cyberciti.biz/faq/ubuntu-20-04-add-network-bridge-br0-with-nmcli-command/


https://bobcares.com/blog/virtualbox-ssh-nat/
ssh -p 2522 ubuntu18@127.0.0.1
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
