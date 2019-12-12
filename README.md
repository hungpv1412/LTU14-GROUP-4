# ChatRoomFX
JavaFX ChatRoom using JAVA RMI

# Important Notes : 
- Create a database(MySQL) and create the "Users" table using "DBScript" file.
- Change the "dbSettings/settings.properties" file as to your database configurations for the server.
 
  (PublicChatServer>dbSettings)
- Use the registry-port as 4000 (Recommended) or change the source code accourdingly in Server's Main class (ServerMain).

# Executing 
*** Take note that the current implementation requires you to run the artifacts (jar files) instead of running the "main" classes 
using the IDE (To avoid "FileNotFound execeptions for resources") -> Otherwise change the source code accordingly*** 

# IDE - IntelliJ IDEA
# Docker config
Run server on docker 
Component:  - mysql:latest
            - openjdk:13
Build :
ENV dbDrive=com.mysql.jdbc.Driver dbConnectionUrl=jdbc:mysql://mysql-chat-server:3306/publicChat dbUserName=root dbPassword=<your pass>
    
*** Build mysql 
docker run -p 3306:3306 --name mysql-chat-server -e MYSQL_ROOT_PASSWORD=<your pass> -d mysql:latest
*** build server
docker run -p 8086:8086 --name chat_server_0.1 --link mysql-chat-server:mysql -d chat_server:0.1 --attach
*** 
Run client and config dbSettings/settings.properties to connect server ip in server in docker