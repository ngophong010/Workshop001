---
title : "Getting Hands-On with Python & Network"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---
### Getting Hands-On with Python & Network
In this final section of Networking fundamentals, we are going to cover some automation tasks and tools with our lab environment created on [Building our Lab](/6-BuildingOurLab)

We will be using an SSH tunnel to connect to our devices from our client vs telnet. The SSH tunnel created between client and device is encrypted.

### Access our virtual emulated environment
For us to interact with our switches we either need a workstation inside the EVE-NG network or you can deploy a Linux box there with Python installed to perform your automation ([Resource for setting up Linux inside EVE-NG](https://www.youtube.com/watch?v=3Qstk3zngrY)) or you can do something like me and define a cloud for access from your workstation.
![Building our Lab](/Workshop001/images/7.hands-On/001-lab.png) 

To do this, we have right-clicked on our canvas and we have selected network and then selected "Management(Cloud0)" this will bridge out to our home network.
![Building our Lab](/Workshop001/images/7.hands-On/002-lab.png) 

However, we do not have anything inside this network so we need to add connections from the new network to each of our devices. (My networking knowledge needs more attention and I feel that you could just do this next step to the top router and then have connectivity to the rest of the network through this one cable?)

I have then logged on to each of our devices and I have run through the following commands for the interfaces applicable to where the cloud comes in.

```plaintext
enable
config t
int g0/0
IP add DHCP
no sh
exit
exit
sh ip int br
```

The final step gives us the DHCP address from our home network. My device network list is as follows:

| Node    | IP Address     | Home Network IP   |
|---------|----------------|-------------------|
| Router  | 10.10.88.110   | 192.168.169.115   |
| Switch1 | 10.10.88.111   | 192.168.169.178   |
| Switch2 | 10.10.88.112   | 192.168.169.193   |
| Switch3 | 10.10.88.113   | 192.168.169.125   |
| Switch4 | 10.10.88.114   | 192.168.169.197   |

#### SSH to a network device
With the above in place, we can now connect to our devices on our home network using our workstation. I am using Putty but also have access to other terminals such as git bash that give me the ability to SSH to our devices.

Below you can see we have an SSH connection to our router device. (R1)
![Building our Lab](/Workshop001/images/7.hands-On/003-lab.png) 

#### Using Python to gather information from our devices
The first example of how we can leverage Python is to gather information from all of our devices and in particular, I want to be able to connect to each one and run a simple command to provide me with interface configuration and settings. I have stored this script here [netmiko_con_multi.py](/Scripts/netmiko_con_multi.py)

Now when I run this I can see each port configuration over all of my devices.
![Building our Lab](/Workshop001/images/7.hands-On/004-lab.png) 

This could be handy if you have a lot of different devices, create this one script so that you can centrally control and understand quickly all of the configurations in one place.

#### Using Python to configure our devices
The above is useful but what about using Python to configure our devices, in our scenario we have a trunked port between `SW1` and `SW2` again imagine if this was to be done across many of the same switches we want to automate that and not have to manually connect to each switch to make the configuration change.

We can use [netmiko_sendchange.py](/Scripts/netmiko_sendchange.py) to achieve this. This will connect over SSH and perform that change on our `SW1` which will also change to `SW2`.
![Building our Lab](/Workshop001/images/7.hands-On/005-lab.png) 

Now for those that look at the code, you will see the message appears and tells us sending configuration to device but there is no confirmation that this has happened we could add additional code to our script to perform that check and validation on our switch or we could modify our script before to show us this. [netmiko_con_multi_vlan.py](/Scripts/netmiko_con_multi_vlan.py)
![Building our Lab](/Workshop001/images/7.hands-On/006-lab.png) 

#### Backing up your device configurations
Another use case would be to capture our network configurations and make sure we have those backed up, but again we don't want to be connecting to every device we have on our network so we can also automate this using [backup.py](/Scripts/backup.py). You will also need to populate the [backup.txt](/Scripts/backup.txt) with the IP addresses you want to backup.

Run your script and you should see something like the below.
![Building our Lab](/Workshop001/images/7.hands-On/007-lab.png) 

That could be me just writing a simple print script in python so I should show you the backup files as well.
![Building our Lab](/Workshop001/images/7.hands-On/008-lab.png) 

#### Paramiko
A widely used Python module for SSH. You can find out more at the official GitHub link [here](https://github.com/paramiko/paramiko)

We can install this module using the `pip install paramiko` command.
![Building our Lab](/Workshop001/images/7.hands-On/009-lab.png) 

We can verify the installation by entering the Python shell and importing the paramiko module.
![Building our Lab](/Workshop001/images/7.hands-On/010-lab.png) 

#### Netmiko
The netmiko module targets network devices specifically whereas paramiko is a broader tool for handling SSH connections overall.

Netmiko which we have used above alongside paramiko can be installed using `pip install netmiko`

Netmiko supports many network vendors and devices, you can find a list of supported devices on the [GitHub Page](https://github.com/ktbyers/netmiko#supports)

#### Other modules
It is also worth mentioning a few other modules that we have not had the chance to look at but they give a lot more functionality when it comes to network automation.

`netaddr` is used for working with and manipulating IP addresses, again the installation is simple with `pip install netaddr`

you might find yourself wanting to store a lot of your switch configuration in an excel spreadsheet, the `xlrd` will allow your scripts to read the excel workbook and convert rows and columns into a matrix. `pip install xlrd` to get the module installed.

Some more use cases where network automation can be used that I have not had the chance to look into can be found [here](https://github.com/ktbyers/pynet/tree/master/presentations/dfwcug/examples)
