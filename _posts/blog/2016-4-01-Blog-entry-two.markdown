---
layout: post
title:  "A simple SocketIO chat with Angular"
date:   2016-4-01 10:51:11
categories: blog
---

In my recent programming adventures, I've noticed the increasing popularity of Websockets and real time data
display. So I decided to go learn SocketIO and with it, I built out a simple real time chat app utilizing
Angular for the front end.

* **Github Repository**: [AngularSocketChat](https://github.com/DeeHKim/angularSocketChat)

One interesting thing about websockets is that when emitting a broadcast to all other connected clients, the
data doesn't actually come back to your own client.

```javascript
io.on('connection', function(socket){

  socket.on('chat', function(message){
    console.log(message);
      socket.broadcast.emit('message', message);
  });
  socket.emit('message', 'HIIII');
});
```

So once the server hears the incoming 'chat' from the client side, it broadcasts that information
to all other clients, but the sender actually doesn't receive back that information. Therefore I had to
update the client's chat display directly when a client was sending his own message.

Websockets seem to be changing the industry standard when it comes to app building, as real time data transfer
and display seems to be in demand.

You can also check out one of the projects I've been working on where we utilized websockets to display real
time data updates on both a chat feature and a board productivity feature:

* **Github Repository**: [TownHall](https://github.com/TownHalls/TownHall)

* **Website Url**: [TownHall](townhallapp.net)
