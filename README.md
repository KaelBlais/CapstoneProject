# CapstoneProject

The purpose of this project was to create an indoor positioning system using the RSS(Received Signal Strength) of custom-built chips. 
For this experiment, various raspberry pis were placed in an indoor environment.
Each raspberry pi was connected to a XBEE module, which a wireless transmitter to communicate with the other raspberry pis. 
The XBEE module also provided the ability to poll all surrounding modules for their RSS. 
This RSS information was collected for every node in the mesh network and fed into a central computer, which used that to calculate location. 
By using a fixed location for some of the nodes, the computer program was able to convert that RSS information into a distance which was then used to triangulate a location. 

This portion of the project is the part that I personally worked on. It encompasses two different programs. 
One of them is the NodeProgram, which is the executable that ran on the Raspberry Pis. 
This was a simple Linux application that opened a serial connection to the XBEE module over the USB port and polled it for its information. 
This made use of the open-source SerialStream library to communicate with the module. 
The NodeProgram also checked for network commands from the computer, to which it would respond with the node's RSS information.
This repository includes the Linux startup scripts used to make the raspberry pis boot off of this program by default. 

The other portion is the ComputerProgram, which was responsible for polling all nodes in the network for their information. 
This would also use an XBEE module to communicate with the other nodes. This communication was done using the Serial.h Windows library. 
This would also manage the mesh network of all active nodes and display their information. 
This then uploaded the information to a TCP socket, which was used for the positioning algorithm. 
The positioning algorithm was done by other group members and is therefore not present in this repository. 
