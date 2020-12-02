# Mysql_Docker_Workbench
running mysql inside docker and using in workbench


# First you need to pull the docker mysql image 
docker pull mysql

# When after pulling mysql you need to create the mysql instance with appropiate info as follow, here i have map my port 3220 to 3306 and can chose the mysql version
 docker run -p 3220:3306 --name mysql-local -e MYSQL_ROOT_PASSWORD=test -d mysql/mysql-server:5.6.44
 
 # after you create this you can see it is running or not in docker dashboard or by command
 docker ps
 
 # But you cant access mysql from you pc as it is running inside docker container localhost so you need to map to be access from you pc or workbench, running this command you will enter
 inside docker machine 
 docker exec -it  mysql-local /bin/bash
 
 # Now log into mysql inside docker
 mysql -uroot -p test
 
 # Now you need to map root user to access not only from docker localhost but from everywhere 
 select user,host from mysql.user; \
 update mysql.user set host='%' where user='root';\
 flush priviliges;
 exit;
 
 # Now you can connect to mysql workbench using hostname as localhost and port as defined by you.
