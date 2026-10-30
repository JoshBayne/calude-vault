## What is a networking model
Networking models categorize and provide a structure for networking protocols and standards

Protocol - set of rules defining how network deivices and software should work

## Networks without standardization
Each manufacturer could have different methods of communicating between clients, meaning for example a mac couldnt talk to a pc

## Open Systems Interconnection Model
Conceptual model that categorizes and standardizes different functions of a network
Created by the International Organization for Standardization (ISO)
Divided into 7 Layers
7. Application
6. Presentations
5. Session
4. Transport
3. Network
2. Data Link
1. Physical

Layers work together
Network engineers don't work with the top 3 Layers (7-5)
Application devs work with top layers of OSI model to connect their apps over networks

### 7. Application Layer
Closest to End User
Interacts with software apps, like a web browser
HTTP and HTTPS are Layer 7 protocols
Functions include
- Identify communication partners
- synchronizing communication

### 6. Presentation
Data in the application is in "application format"
Needs to be translated to a different format
Presentation layer translates between application adn network formats
ex. encyption of data as it is sent, and decryption on arrival
Translates between different L7 formats

### Session
Controlls dialogues (sessions) between communication hosts
Establishes manages and terminates connections between local app like a browser and a remoteapp like youtube

### Transport
Segments and reassembles data between end hosts during communications
(chunks data into segments to be more easily sent over network, ensures less transmission errors)
Provides Host-to-host communication (end-to-end)

### Network
Proovides connectivity between end hosts on different networks
Provides Ip addresses (logical addresses)
Provides path selection between source and destination
Routers work on L3

### Data Link
Provied node-to-node connectivity and data transfer (pc to switch, switch to router, router to router)
Defines how data is formatted for transmission over physical medium (ex.copper UTP cables)
detects and maybe corrects L1 errors
Uses L2 addressing, different from L3
Switches operate on L2

### Physical
Defines physical characteristics of the medium used to transfer data
for example, voltage levels, max transmission distances, physical connectors, specs, etc
digital bits are converted to electrical or radio signals
all of the information from [[2 - Interfaces and cables]] is related to L1

## OSI model - PDUs
Data
Segment, data with layer 4 header
Packet - Data with L3 and L4 headers
Frame - data with L2 header/trailer, L3 and L4 headers
All are PDUs (protocol data units)
layer 1 PDU is bit

## OSI model Acronyms
All people seem to need data processing
or
Please do not teach students pointless acronyms

## TCP/IP Suite
Conceptual model and set of communications protocols used in the internet and other networks
known as TCP/IP because those are two of the foundational protocols in the suite
developed by DARPA
similar structure but fewer layers than OSI
Model actually used today in modern networks
OSI still influences modern network lingo

4. Application
	- similar to layers 7-5 of the OSI model
3. Transport
	- similar to layer 4 of OSI model
2. Internet
	- Maps to the Network layer (3) of OSI model
1. Link
	- Equivalent to Layers 2 and 1 of OSI model

