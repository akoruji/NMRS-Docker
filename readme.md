# You will require internet connection to run this installation!

# This app will create 2 instances of NMRS on docker.
The docker-compose.yml file contains the configuration variables that can be adjusted as required. Inside you can see the Tomcat services and images and MySQL services and images. You can also see the various ports. You can configure the .yml file to increase or decrease the number of NMRS instances as required but be mindful of system resources.

# To buid the appliation:
Open a terminal or dommand prompt inside the current directory and type:
docker-compose up -d

# To tune the MySQL performance: 
When the MySQL container is running, you can edit the etc/my.cnf file in the Docker root directory.
Remember to create users and grant privileges before importing your database.

# To add modules:
When the tomcat container is running, go to root/.OpenMRS/modules

# Note: 
You may need to add the following to the tomcat and mysql services in docker-compose.yml file to autostart. 
restart: always

# Manual Timezone Configuration

The timestamps in the log seem to show two different time zones or formats:
2025-01-06 15:24:16 - The time logged by the application.
2025-01-06 14:24:16,675 - The time from the container which is 1 hour behind.

To align these times, you can adjust the timezone or ensure consistent time settings across your environment.
If your container is Alpine-based (the OS we used to develop the docker images), follow these steps:

1. Access the running container:
docker exec -it <container-id> /bin/sh
2. Update apk and install tzdata (timezone data package):
apk update
apk add tzdata
3. Set the timezone:
Copy the Africa/Lagos timezone file to /etc/localtime:
cp /usr/share/zoneinfo/Africa/Lagos /etc/localtime
4. Verify the Change: Type the date command to confirm the timezone is updated:
date


