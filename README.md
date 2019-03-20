# cisco-ansible-test01

The lab was done in GNS3.

##### Cisco image:

1. vios_l2-adventerprisek9-m, version 15.2(20170321:233949)


##### Ansible controller requirements:

1. ansible
2. dnsmasq
3. git

##### Clone the repo:
`https://github.com/rynldtbuen/cisco-ansible-test01.git`

##### Initial configurations of deployment device:

Note: Because we are using a VIOS we cannot simulate a AutoInstall feature on Cisco IOS device therefore just to simulate the process of AutoInstall we need to additonal configuration on the deployment device. In AutoInstall we don't need this configuration.

1. Setup your network.

1. Enable the device to obtain config files from tftp server.

`service config`

2. Configure the management interface (usually connected to out-of-band management switch)
   of the deployment device to obtain ip address from dhcp server. While in interface configuration copy
   the hardware address of the management interface and paste in the ansible inventory file named 'devices' 
   into a 'mgmt_hwaddr' variable
   
```
! Change the commands accordingly
interface GigabitEthernet0/0
 no switchport
 ip address dhcp
```

3. Save the changes and reload the device

##### Run Ansible playbook

1. Edit the ansible inventory and variables as per your requirements and setup

`ansible-playbook save_running_config`
