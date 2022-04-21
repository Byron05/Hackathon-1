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
### Server and Client: ###
* This real-time chat functionality is accomplished through a bi-directional communication channel, meaning that the server can send data back to the client independently without any requests. There are 3 specific event handlers to listen to, respectively to send a message, join a room, and leave a room:
```
def handle_send_message_event(data):
    app.logger.info("{} has sent message to the room {}: {}".format(data['username'],
                                                                    data['room'],
                                                                    data['message']))
    socketio.emit('receive_message', data, room=data['room'])
```
```
@socketio.on('join_room')
def handle_join_room_event(data):
    app.logger.info("{} has joined the room {}".format(data['username'], data['room']))
    join_room(data['room'])
    socketio.emit('join_room_announcement', data, room=data['room'])
```
```
@socketio.on('leave_room')
def handle_leave_room_event(data):
    app.logger.info("{} has left the room {}".format(data['username'], data['room']))
    leave_room(data['room'])
    socketio.emit('leave_room_announcement', data, room=data['room'])
```
* The user will first be prompted to log in with a name to be displayed, followed by being able to join a chat room, see who joins, and chat with multiple people at once.

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

