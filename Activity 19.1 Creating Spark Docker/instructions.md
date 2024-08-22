Spark is a complex application with several components, and installing it can be challenging. Luckily, there are a few Spark Docker images that are available for you to use. Dr. Sanchez mentions two of these Spark Docker images in Video 19.2: Big Data Europe and Bitnami. You will be using the Docker image provided by Bitnami for this activity.

Prior to beginning this activity, review the submission instructions below to ensure that you collect the required screenshots as you progress through the activity.

To complete this activity, follow these steps:

Open Docker Desktop on your machine. Provide a screenshot to show that you have no containers running.
Create a new folder called bitnami. Provide a screenshot to show that you successfully created the bitnami folder.

Open a command prompt window and navigate to the bitnami folder. Run the following curl command to download the docker-compose.yml file:

`curl https://raw.githubusercontent.com/bitnami/containers/main/bitnami/spark/docker-compose.yml -o docker-compose.yml`

Provide a screenshot to show that you successfully ran the curl command to download the docker-compose.yml file.

List the contents of the bitnami folder to verify that the docker-compose.yml file has been created. Provide a screenshot to show the contents of the Spark folder within the docker-compose.yml file.

From the command prompt inside the bitnami folder, run the following command:

`docker-compose up`

Provide a screenshot to show that you successfully ran the docker-compose command.

Provide a screenshot of your Docker Desktop to show that the Spark Docker containers are running.

Open your browser to the following URL:

http://localhost:8080/

Provide a screenshot to show that you successfully opened your browser to the Spark webpage. 

Congratulations. You have successfully completed Activity 19.1 to set up a Spark Docker container and you are now ready to start working with Spark.