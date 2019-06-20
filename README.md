# Chat application using WenSocket
A chat app using WebSockets
# What are WebSockets
- Une communication entre un client et un serveur, ou les données circulent dans les deux directions (client/serveur ou serveur/client) ce qui permet une communication en temps réel client serveur (du fait que la communication est toujours ouvert)
- Par exemple dans cette applications de chat, on a un serveur qui héberge notre application, tous les clients se connectent a ce serveur pour échanger, lorsque un client se connecte sur le serveur il va avoir la page web en plus de l'ouverture du canal de communication (chaque client a son propre socket)
- La communication s'effctue sans utiliser de l'AJAX
- Use cases:
    - Multiplayer browser games
    - Collaborative code editing
    - Online drawing canvas

# Code
Il faut importer le bibliothéque **socket.io.js** soit côté client ou bien côté serveur

## Client
A standalone build of **socket.io-client** is exposed automatically by the socket.io server as _/socket.io/socket.io.js_
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/1.7.3/socket.io.js"></script>
```
```
// Make connection
var socket = io.connect('http://localhost:4000');
```
## Server
```
npm install --save socket.io
```
```
var socket = require('socket.io');
var server = app.listen(4000, function(){
    console.log('listening for requests on port 4000,');
});
// open server connection
var io = socket(server);
// listen for clients
io.on('connection', (socket) => {

});
```
## What are the disadvantages of using traditional HTTP request response communication model?

- **Traditional HTTP requests are unidirectional**: In traditional client server communication, the client always initiates the request.
- **Heavy**: Normal HTTP request and response require exchange of extra data between client and server.

## What are the advantages of using WebSockets over traditional HTTP communication? 
- **WebSocket are bi-directional**: Using WebSocket either client or server can initiate sending a message.
- **Light**: The WebSocket message data exchange is much lighter compared to http.

## Vanilla websockets vs socket.io
- socket.io is a library to work with websockets
- WebSocket does not support braodcasting, socket.io does
- Native websockets provide us with only a send method to send data to the server. Send accepts only string input (not too sure about this). Socket.io lets us emit arbitrary events with arbitrary data (even binary blobs) to the server.
- Vanilla websocket client will not work on browsers that don't support it (think IE8, IE9, Opera Mini) but a socket.io client server pair will since it has fallbacks



