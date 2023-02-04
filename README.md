# CHATROOM

chatroom is a nodejs app that use socket.io, express library.

## Installation

use the package socket.io, express, ejs and nodemon
```bash
npm install socket.io express ejs nodemon --save
```

### How to create server?
```js
const express = require("express");
const socketio = require("socket.io");
const app = express();

app.set("view engine", "ejs");
app.use(express.static("public"));

app.get("/", (req, res) => {
  res.render("index");
});

const server = app.listen(process.env.PORT || 3000, () => {
  console.log("server is running...");
});

// Initialize socket for the server
const io = socketio(server);

io.on("connection", (socket) => {
  console.log("New user connected");
});
```

### How to create client?
```js
(function connect() {
  let socket = io.connect("http://localhost:3000");
  console.log("connected!")
})();
```