# -----Distributed Server Consistency check application-----

java version : 1.8 OS : linux

Referenced Libraries :

Thrift - 0.9.3 SLF4J - 1.7.21

To compile just type:

javac -cp ".:./Referenced_Libraries/slf4j-simple-1.7.21.jar:./Referenced_Libraries/slf4j-api-1.7.21.jar:./Referenced_Libraries/libthrift-0.9.3.jar" App/*.java

OR

You can also compile by Executing the shell script ./kvCompile.

To run client just type:

java -cp ".:./Referenced_Libraries/slf4j-simple-1.7.21.jar:./Referenced_Libraries/slf4j-api-1.7.21.jar:./Referenced_Libraries/libthrift-0.9.3.jar" App.CheckServer -server 192.168.1.5:9634

Server will run by default on localhost, port 5000.

You can also run the client by Executing the shell script ./consistency_test -server 192.168.1.5:9634.

The client and server are built using java and You just need to run the consistency_test script to run the application with appropriate arguments.

Internal Working:
Initialize a default value on the server. Then, start 20 threads / clients which randomly set and get values. Then, Time edge is added according to the algorithm presented in the paper*. Then data and Hybrid edge is added to the graph. After that, cycle detection algorithm is run to check the presence of cycle. If cycle is not found then it can be concluded that the server is consistent else it is inconsistent.

* Paper referred: http://www.hpl.hp.com/techreports/2010/HPL-2010-98.pdf
