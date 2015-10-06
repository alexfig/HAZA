# INCARNADINE-PHAROAH

A game where cells eat other cells.

# Steps to run
1. From root directory: npm install
2. From client directory: bower install
3. Create an agar database for MySQL (can be done from any directory)
   - On macs, mysql -uroot <password> (this should open the MySQL command line interface)
   - CREATE DATABASE agar; (type this in MySQL and verify the database has been created)
4. Change the root password for MySQL in the DB folder
   - Open up ./DB/models.js
   - Change the third parameter in the Sequelize constructor to be your root MySQL password
5. Run the server
   - From the parent directory, run the following command: node ./server/server.js
   - Watch terminal for server messages based on user logins and server errors

# Directory layout
# ./DB/
models.js:
   - This file uses Sequelize to create a tables in the database used by the game, assuming the 'agar' database is instantiated.

# ./server/
db-helpers.js:
   - This file compliments the ./DB/models.js file defined above. It acts as a helper interface for performing userful queries on tables defined in the database. Some of this queries involve user login/signup verifications, finding friends, and looking up the statistics about a player's historic performance in previous games played (statistics are not currently used, but the functionality is there).

server.js:
   - This file acts as the server itself. The server is built using http://socket.io/, and server.js handles user connections, disconnects, and event listeners for client functionality like adding friends, sending game data, and receiving game data.

game.js:
   - This file is essentially where all of the current data the server is holding is stored. exports.roomData holds all of the information about the current game rooms up and running. Additionally, game.js holds exports.sockets, which holds essential user information for every socket that is connected to the server. Also, exports.onlineUsers is an object mapping online users to their connected socket.id. Lastly, exports.foodData stores information about the food on the server, where the key for each key value pair is a roomName, and the value is the foodData for the associated roomName object in exports.roomData.rooms[roomName].

# ./client/
This folder holds all of the front end code, including index.html, front end JavaScript, and CSS. indexApp.js is responsible for creating the initial Angular app, which uses an extension of SocketIO for angular: https://github.com/btford/angular-socket-io. Essentially, this SocketIO extension works exactly as you would expect SocketIO to be implemented.

# ./client/js/angularControllers
This folder holds all of the data for the https://angularjs.org/ usage. Controllers are identified by the corresponding div that they handle on the index.html page.

# ./client/js/game
This folder holds all of the code for the use of the Phaser game engine: http://phaser.io/. The result from the engine code is rendered on the gameDiv div in the index.html page.
