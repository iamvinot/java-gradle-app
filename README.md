##### build the project

    ./gradlew build

##### build Docker image called java-app. Execute from root

    docker build -t java-app .
    
   ## CI/CD 
   
 #### start TeamCity server as docker 
 
    docker run \
    -v team_city_data:/data/teamcity_server/datadir \
    -v team_city_logs:/opt/teamcity/logs  \
    -p 8111:8111 \
	-d jetbrains/teamcity-server
    

#### start TeamCity agent with docker volume mount

    docker run --name ta1 -d -e SERVER_URL="http://publicIP:8111" \
    -u 0 \
    -v ta1_config:/data/teamcity_agent/conf \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /usr/bin/docker:/usr/bin/docker \
    jetbrains/teamcity-agent
      
