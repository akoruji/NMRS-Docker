# This installation requires internet connection.

# This app will create 2 (or more) instances of NMRS on docker.
The docker-compose.yml file contains the configuration variables that can be adjusted as required. Inside you can see the Tomcat services and images and MySQL services and images. You can also see the various ports. You can configure the .yml file to increase or decrease the number of NMRS instances as required but be mindful of system resources.

# To buid the appliation:
Open a terminal or command prompt inside the current directory and type:
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

# For more deatils on how to get started with NMRS on Docker:
1. Install Docker desktop for windows. [Click here to learn more.](https://docs.docker.com/desktop/install/windows-install/)
2. Create a docker-compose.yml file [Click here to learn more.](https://github.com/ihvn2020/NMRS-POC-Docker/tree/main/Create%20docker-compose%20yml%20files)
3. Create a Dockerfile [Click here to learn more.](https://github.com/ihvn2020/NMRS-POC-Docker/tree/main/Create%20Dockerfile)
4. [Click here to download the complete installation guide.](https://github.com/ihvn2020/NMRS-POC-Docker/blob/main/NMRS%20INSTALLATION%20USING%20DOCKER%20ON%20WINDOWS.docx)

# References
https://docs.docker.com/get-started/
https://docs.docker.com/desktop/install/windows-install/
https://wiki.openmrs.org/display/docs/Installing+OpenMRS+on+Docker

# Project Team
1. Bright Ibezim (Team Lead)
2. Abdulmojeed Akande
3. Temitayo Raimi
4. Oluwadamilare Adebawo
5. Akor Uji
6. Kolawole Adesoji
7. Tochukwu Emeka
8. Halima Baba
