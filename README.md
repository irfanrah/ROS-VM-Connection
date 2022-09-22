# ROS-VM-Connection

```
1. You need to change the network on Virtual Machine, 
because NAT network (default) is not compatible with ROS communication
http://wiki.ros.org/win_ros/Tutorials/WinRos%20and%20Virtual%20Ubuntu
go to File > Host Network Manager > and set up a new profile like this

After that, you can change the VM slave connection to Host-only Adapter
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/3.png" width=50% height=50%>
</p>


<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/1.png" width=50% height=50%>
</p>


```
2. Check your ip with ifconfig in terminal
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/2.png" width=50% height=50%>
</p>


```
3. Setup VM slave localhost with 
sudo nano /etc/hosts
add your ip and name on there
don't forget to close the terminal and reopen again
```

```
4. Activate SSH in both machine
systemctl status ssh
sudo apt-get install openssh-server
sudo systemctl enable ssh --now
```

```
5. Test the SSH connection between two machine
ssh [computer_name]@[computer ip]
ssh irfanrah@192.168.56.1
ssh ubuntu18@192.168.56.101
if it's working and able to access both machine, you can proceed to the next step
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
7. Multiple machine setup
http://wiki.ros.org/ROS/Tutorials/MultipleMachines

a. In master machine 
nano ~/.bashrc
export ROS_MASTER_URI=http://192.168.56.1:11311
export ROS_HOSTNAME=192.168.56.1

b. In slave machine
export ROS_MASTER_URI=192.168.56.1:11311
export ROS_HOSTNAME=192.168.56.101
export ROS_IP=192.168.56.101
```
<p align="center">
<img src="https://github.com/irfanrah/ROS-VM-Connection/blob/main/pics/4a.png" width=50% height=50%>
</p>


```
8. Check it;s working
a. master machine
roscore
cd catkin_ws/src/scripts
sudo chmod +x listener.py
./listener

b. slave machine : 
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
