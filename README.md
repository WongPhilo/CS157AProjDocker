# CS157AProjDocker
First, you'll need to have the Docker Engine installed and running. Then, open a terminal in the directory where fishmarket.tar is located, or on some parent directory that has access.

In order to load the image:

docker load -i fishmarket.tar

Now, in order to start the MySQL server, run with the public Docker image:

docker run -d --rm --name=sql-server -e MYSQL_ROOT_PASSWORD=123 mysql

To check that server is running:

docker ps

To check the IP address of server (to be used in the client):

docker inspect sql-server

To run the client (on my end, the server IP address is 172.17.0.2):

docker run -it --rm fishmarket mysql -h172.17.0.2 -uroot -p123

Running on Windows, you'll have to use this:

docker run -it --rm fishmarket mysql -h"172.17.0.2" -uroot -p123

To build and populate the tables, run the following commands:

source create.sql
source insert.sql
source views.sql

Now you can input standard MySQL commands into the terminal, and receive results. Remember that inputs are case-sensitive, and that all of my entities and attributes are upper-case!

This image was created and runs fine on Ubuntu 22.04, but I've tested it and it works fine on Windows too.  

