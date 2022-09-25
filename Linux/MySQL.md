From Digital Ocean

Install MySQL: 

First let's use `sudo apt update` to get and be sure you've the latests updates.

Then `sudo apt install mysql-server`

To launch MySQL the command is `sudo mysql -u root -p`.

Now we're going to create an user by doing : `CREATE USER 'username'@'localhost' IDENTIFIED BY 'thepasswordyouwant'*;* (Do not forget the ";" at every end of command that you use in MySQL).

Let's grant privileges now : `GRANT ALL PRIVILEGES ON *.* (for example wordpress.* => grants access to all the wordpress database) TO 'username'@'localhost' WITH GRANT OPTION;`

CONGRATS you installed MySQL!
