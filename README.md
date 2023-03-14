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

This Router is connected to three networks (200.4.1.0-200.4.2.0-200.4.5.0) so we need to configure three interfaces FastEthernet Fa0/0 with an ip add 200.4.1.1, FastEthernet Fa1/0 with an ip add 200.4.2.1 and a Serial interface Se3/0 with an ip add 200.4.5.1 . then we use the no shutdown command to enable these interfaces. the last thing we write is the copy running command to save our configuration .

- we can perform this configuration using two methods :
  
  - gui :
  
  ![image](https://user-images.githubusercontent.com/121964432/224856772-644f485e-afea-4d8b-a876-41157f293cb9.png)
  
  ![image](https://user-images.githubusercontent.com/121964432/224859746-fd8f8bd1-06ca-45c9-8d86-a424f41709b9.png)
  
  ![image](https://user-images.githubusercontent.com/121964432/224859804-2b3637d5-ee2f-465d-bbbd-f6128845794d.png)


  - CLI :
  
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

## Router 2 (R2)

This Router is connected to three networks (200.4.5.0-200.4.3.0-200.4.6.0) so we need to configure three interfaces FastEthernet Fa0/0 with an ip add 200.4.3.1, Serial interface Se2/0 with an ip add 200.4.5.2 and a Serial interface Se3/0 with an ip add 200.4.6.1 . then we use the no shutdown command to enable these interfaces. the last thing we write is the copy running command to save our configuration .

- for the configuration its the same thing we did for the first router :
   - gui :
   
     ![image](https://user-images.githubusercontent.com/121964432/224859692-71dfd977-0c80-4a7a-916b-4ce77424f148.png)

     
     ![image](https://user-images.githubusercontent.com/121964432/224859597-ef82efe9-a877-4030-9532-da2c634a7f7a.png)
     
     ![image](https://user-images.githubusercontent.com/121964432/224859631-2600739b-0f58-4da3-aeb6-45524b9436c6.png)



   - CLI :

```cmd
Router(config)#interface Serial2/0
Router(config-if)#ip address 200.4.5.2 255.255.255.0
Router(config-if)#
Router(config-if)#exit
Router(config)#interface Serial3/0
Router(config-if)#ip address 200.4.6.1 255.255.255.0
Router(config-if)#
Router(config-if)#exit
Router(config)#interface Fa0/0
Router(config-if)#ip address 200.4.3.1 255.255.255.0
Router(config-if)#
Router(config-if)#exit
Router(config-if)# no shutdown
Router(config)# copy running startup
```

## Router 3 (R3)

This Router is connected to three networks (200.4.6.0-200.4.4.0) so we need to configure two interfaces FastEthernet Fa0/0 with an ip add 200.4.4.1 and a Serial interface Se2/0 with an ip add 200.4.6.2 . then we use the no shutdown command to enable these interfaces. the last thing we write is the copy running command to save our configuration .

- for the configuration its the same thing we did for the first router :
   - gui :
   
     ![image](https://user-images.githubusercontent.com/121964432/224858079-9bc2c4da-eabd-4b7e-bbc0-b4387776f9c8.png)
     
     ![image](https://user-images.githubusercontent.com/121964432/224859555-284867e7-600d-4f76-9899-a733d7164b93.png)


   - CLI :

```cmd
Router>enable
Router#
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface FastEthernet0/0
Router(config-if)#ip address 200.4.4.1 255.255.255.0
Router(config-if)#ip address 200.4.4.1 255.255.255.0
Router(config-if)#
Router(config-if)#
Router(config-if)#exit
Router(config)#interface FastEthernet0/0
Router(config-if)#no shutdown
Router(config-if)#
%LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up

Router(config-if)#exit
Router(config)#interface Serial2/0
Router(config-if)#ip address 200.4.6.2 255.255.255.0
Router(config-if)#ip address 200.4.6.2 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#ex
Router(config)#copy running startup
```
  
# Test :
 
now lets perform some tests 
 
first we are going to ping the pc with the ip add 200.4.2.2 using the one with the ip add 200.4.1.2 
 
 ![Capture d’écran 2023-03-13 230127](https://user-images.githubusercontent.com/121964432/224858486-71752c83-958f-4c09-b2de-7cd8184173c0.png)


as you can see its working , Now lets try to ping the pc with the ip add 200.4.3.2

![Capture d’écran 2023-03-13 230059](https://user-images.githubusercontent.com/121964432/224858593-fa697583-9a30-46f6-b714-a675bbe06dfb.png)

we can not reach the destination and thats because we didnt do the routing yet and this is going to be our next step 

# Routing :

When a data packet is sent from one device to another on a network, it is first received by the router that is connected to the sender's network. The router then examines the packet's destination address and looks up the best route for the packet to reach its destination. This involves consulting a routing table, which contains information about the network topology, available bandwidth, congestion, and other network conditions.
Now lets add the necessary routes for R1 :

```cmd
R1(config)#ip route 200.4.6.0 255.255.255.0 200.4.5.2
R1(config)#ip route 200.4.3.0 255.255.255.0 200.4.5.2
R1(config)#ip route 200.4.4.0 255.255.255.0 200.4.5.2
```
 
 ![image](https://user-images.githubusercontent.com/121964432/224860680-a36319a2-35bc-4173-9b9f-fb39dd7544f6.png)

- Router 2 routing :

```cmd
R2(config)#ip route 200.4.1.0 255.255.255.0 200.4.5.1
R2(config)#ip route 200.4.2.0 255.255.255.0 200.4.5.1
R2(config)#ip route 200.4.4.0 255.255.255.0 200.4.6.2
```

![image](https://user-images.githubusercontent.com/121964432/224861069-9901e7ef-ca78-4139-8589-3ce579885070.png)

- Router 3 routing :

```cmd
R3(config)#ip route 200.4.5.0 255.255.255.0 200.4.6.1
R3(config)#ip route 200.4.3.0 255.255.255.0 200.4.6.1
R3(config)#ip route 200.4.2.0 255.255.255.0 200.4.6.1
R3(config)#ip route 200.4.1.0 255.255.255.0 200.4.6.1
```

![image](https://user-images.githubusercontent.com/121964432/224861229-87f25007-47d8-450a-af1c-e08d8c7c0b08.png)

