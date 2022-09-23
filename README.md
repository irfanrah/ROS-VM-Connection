# ROS-VM-Connection
### Objective
The objective of this repo is to enable ROS communication between master and slave with Virtual Box settings, I found there are no clear tutorials about this, so this repository may help you.

### Ground Rules
* Ubuntu 20 with ROS Noetic as Master and LAN Internet connection
* Ubuntu 18 with ROS Melodic as Slave in Oracle VM Virtual Box Manager


---
### Step-by-step
```
1. You need to change the network on the Virtual Machine, 
because the NAT network (default) is not compatible with ROS communication

Go to File > Host Network Manager > and create new profile as follows

After that, you can change the VM slave connection to Host-only Adapter
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/3.png" width=50% height=50%>
</p>


<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png" width=50% height=50%>
</p>


```
2. Use ifconfig in terminal to check your IP address
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/2.png" width=50% height=50%>
</p>


```
3. Setup VM slave localhost with 
sudo nano /etc/hosts
add your IP address and name on there
Close and reopen the terminal
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/4.png" width=50% height=50%>
</p>

```
4. Enable SSH in both machine
systemctl status ssh
sudo apt-get install openssh-server
sudo systemctl enable ssh --now
```

```
5. Test the SSH connection between two machines
ssh [computer_name]@[computer ip]
ssh irfanrah@192.168.56.1
ssh ubuntu18@192.168.56.101
If it's working and you may able to access both machines, you can proceed to the next step
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png" width=50% height=50%>
</p>

```
6. Clone this repo in both machine
cd catkin_ws/src
git clone https://github.com/irfanrah/ROS-VM-Connection
```

```
7. Multiple-machines setup

a. In master machine 
nano ~/.bashrc
export ROS_MASTER_URI=http://192.168.56.1:11311
export ROS_HOSTNAME=192.168.56.1
Close and reopen the terminal

b. In slave machine
export ROS_MASTER_URI=192.168.56.1:11311
export ROS_HOSTNAME=192.168.56.101
export ROS_IP=192.168.56.101
Close and reopen the terminal
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/4a.png" width=50% height=50%>
</p>


```
8. Check the communication between Multiple-machines
a. Master machine :
roscore
cd catkin_ws/src/scripts
sudo chmod +x listener.py
./listener

b. Slave machine : 
cd catkin_ws/src/scripts
sudo chmod +x talker.py
./talker
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/5.png" width=50% height=50%>
</p>
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/6.png" width=50% height=50%>
</p>



---
### References 

[here 1](http://wiki.ros.org/win_ros/Tutorials/WinRos%20and%20Virtual%20Ubuntu)  

[here 2](https://kr.mathworks.com/matlabcentral/answers/392422-cannot-connect-to-ros-master-running-on-virtual-machine) 

[here 3](http://wiki.ros.org/ROS/Tutorials/MultipleMachines) 
