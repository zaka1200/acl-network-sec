# acl-network-sec
# Introduction

 in this practical work we are going to create a network where we will trz what we learnt about access list , our network is going to be composed of 3 routers 4 switchs and 8 Pcs , we are going to link and configure each one of them then we will create our access lists .
 
 # network architecture 
  
  using Packet Tracer we created this network
  
  ![Capture d’écran 2023-03-13 221709](https://user-images.githubusercontent.com/121964432/224852564-56dcb079-0f5a-471d-9ac7-1ddaf5f9fb35.png)
  
  > Router : Router-PT
  
  
 > Switch : 2960
 

 
 as you can see the connection is not established , so we need to configure our devices 
 
 # PCs configuration :
 we are going to start by giving each Pc an ip address and specifie the gateway address:
    
  - using gui :
  
  ![image](https://user-images.githubusercontent.com/121964432/224853295-e0e1177b-ff2a-45ff-afe7-e657d52ba6af.png)

 we need to do the same thing for the others :
 
 | PC    | Ip add |
| ----------- | ----------- |
| PC0      | 200.4.1.2       |
| PC1   | 200.4.1.3       |
| PC2      | 200.4.2.2       |
| PC3  | 200.4.2.3       |
| PC4      | 200.4.3.2       |
| PC5   | 200.4.3.3       |
| PC5      | 200.4.4.2       |
| PC7   | 200.4.4.3       |

# Routers :

next devices are the routers we are going to start by the first one :

## Router 1 (R1) :

This Router is connected to three networks (200.4.1.0-200.4.2.0-200.4.5.0) so we need to configure three interfaces FastEthernet Fa0/0 with an ip add 200.4.1.1, FastEthernet Fa0/0 with an ip add 200.4.2.1 and a Serial interface with an ip add 200.4.5.1 . then we use the no shutdown command to enable these interfaces. the last thing we write is the copz running command to save our configuration .

- we can perform this configuration using two methosds :
  
  - gui :
  
  ![image](https://user-images.githubusercontent.com/121964432/224856772-644f485e-afea-4d8b-a876-41157f293cb9.png)

  - commandline :
  
  ```cmd
  Router>enable
Router#
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface FastEthernet0/0
Router(config-if)#ip address 200.4.1.1 255.255.255.0
Router(config-if)#ip address 200.4.1.1 255.255.255.0
Router(config-if)#
Router(config-if)#exit
Router(config)#interface FastEthernet1/0
Router(config-if)#ip address 200.4.2.1 255.255.255.0
Router(config-if)#ip address 200.4.2.1 255.255.255.0
Router(config-if)#
Router(config-if)#exit
Router(config)#interface Serial2/0
Router(config-if)#ip address 200.4.5.1 255.255.255.0
Router(config-if)#ip address 200.4.5.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#
%LINK-5-CHANGED: Interface Serial2/0, changed state to up

Router(config-if)#exit
Router(config)#interface FastEthernet1/0
Router(config-if)#no shutdown
Router(config-if)#ex
Router(config)#copy running startup
  ```
  
  
  
