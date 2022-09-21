# ROS-VM-Connection

1. Activate SSH in both machine
systemctl status ssh
sudo apt-get install openssh-server
sudo systemctl enable ssh --now

2. Test the SSH connection between two machine
check the with ifconfig in terminal
![alt text](https://github.com/irfanrah/ROS-VM-Connection/pics/1.jpg?raw=true)
ssh irfanrah@223.195.39.11
ssh ssh ubuntu18@10.0.2.15

https://bobcares.com/blog/virtualbox-ssh-nat/
ssh -p 2522 ubuntu18@127.0.0.1
