# EC530 Hackathon 1: Secure Peer-to-Peer Chat 

## Team Members:
* [Jami Huang](https://github.com/jamih)
* [Nicole Kwon](https://github.com/nicolekwon)
* [Byron Mitchell](https://github.com/Byron05)
* [Nancy Zheng](https://github.com/nancyzhe)

### Table of Contents:
* [Project Overview](#projectoverview)
* [Server](#server)
* [Running the Project](#runningapp)

<a name="projectoverview"></a> 
### Project Overview: ###
* The objective of this project was to create a secure way for peer-to-peer chat with the following features. 
    * Data will be distributed.  No Data will be stored in a central Server.
    * All local data is stored on clients.
    * All Data stored on the device will be secure.
* We used UDP to implement Peer to Peer messsaging. 
* A rendezvous server was used to facilitate the connection proccess
   
   
<a name="server"></a> 
### Server: ###
* Users can be discovered via a centralized server. This means users can update the IP address for peer to peer communications.
* The client needs to make sure the IP address in discovery server is correct. 
* When a user is discovered, clients can send them any updates or new chats.
* To modify the IP address the user, can navigate to *client.py* and change *'xxx.xx.xx.x'* to their IP address (as seen below). Other users can connect via the server and chat with eat other. 

```
rendezvous = ('xxx.xx.xx.x', xxxxx)
```

<a name="runningapp"></a> 
 ### How to Run the App ###

