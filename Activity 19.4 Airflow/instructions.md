In this activity, you will run your own workflow within Airflow by creating an Airflow Docker container to execute a simple Python function.

Prior to beginning this activity, review the submission instructions below to ensure that you collect the required screenshots as you progress through the activity.

To complete this activity, follow these steps:

Create an empty folder called airflow on your local machine. Navigate to the airflow folder within a Terminal window and pull the Airflow file with the following command:

`curl https://airflow.apache.org/docs/apache-airflow/2.1.1/docker-compose.yaml -o docker-compose.yaml`

Provide a screenshot to show that you successfully ran the command.

Open the generated docker-compose.yaml file. Under "environment", set the AIRFLOW__CORE__LOAD_EXAMPLES variable equal to false. Provide a screenshot to show the changed example value (AIRFLOW__CORE__LOAD_EXAMPLES set to false).

In the Terminal window, run the `docker-compose up` command to start the Airflow Docker container. Open Docker and select the container to see all of the parts. Provide a screenshot of the Docker window to show that Airflow is running. 

Note: This step may take some time to complete. 

In your web browser, navigate to http://localhost:8080/. Log in to Airflow using the default username and password: “airflow”. Provide a screenshot of your browser window to show that you have successfully logged in to Airflow.

Place the SampleDAG.py file in the dags folder. Provide a screenshot of the dags folder to show that the file is present. 

Navigate back to your web browser and confirm that the hello_world DAG is now configured. Provide a screenshot to show that the hello_world DAG is successfully displayed in your Airflow window.

Note: For this step, it may take a few minutes for the DAG to show.

Start the DAG by toggling the switch to the left of its name. Select the DAG and open up the Graph View. Select the DAG again and open “logs”. Provide a screenshot of the log to show that the DAG ran successfully.