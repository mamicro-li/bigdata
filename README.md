# Big Data Final Project
1. Project description:
 
  I build the Mnist hand-written recognition program into a docker container and by applying restful web service API, the           program is able to handle the request from client console and print out the result of prediction of hand-written picture, and   finally post all of the information into Cassandra database which is also built in another container in docker. 
  
2. File description:
 
  Number1-9.png are input hand-written pictures.
  
  Dockerfile, app.py, requirements.txt are files for container creation on Docker.

3. How to run:

(1).docker pull Cassandra                                      (Pull cassandra database to docker)

(2)docker build --tag=restful .                               (Build image and container)

(3)docker network create --attachable test_net                (Create network for container communication)

(4)docker run –-network=test_net --name hongwei-cassandra -p  (Run the cassandra database and connect it to the network) 

(5)docker run –-network=test_net -p 4000:80 restful           (Run the app and connect it to the netwrok we created)
  
  In a new command window:
  
  Command 1:
  
  curl -i http://localhost:80/todo/api/v1.0/tasks               (At the first time running this command: If no keyspace is                           
                                                                created, it will create a new keyspace and a new table, 
                                                                otherwise it does nothing.At the next time running it, it 
                                                                returns all data from the keyspace)
                           
  Command 2:
  
  curl -i -H "Content-Type: application/json" -X POST -d '{"file":"number8.png"}' http://localhost:80/todo/api/v1.0/tasks
  (Input hand-written file,file name followed by "file" in the command and returns the prediction of this picture, and then
  post the result to cassandra database)
  
 
 4. [![Demo video](https://img.youtube.com/vi/j7JceTSyAZ4/0.jpg)](https://www.youtube.com/watch?v=j7JceTSyAZ4)

  


