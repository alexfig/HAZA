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
   
