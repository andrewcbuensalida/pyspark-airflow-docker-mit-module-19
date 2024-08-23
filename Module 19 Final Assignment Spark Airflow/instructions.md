In this assignment, you will demonstrate your understanding of PySpark and Airflow.

The first part of this assignment focuses on PySpark. In the first part of this assignment, you will be required to create PySpark Docker containers using the Bitnami Spark Docker image. Next, you will be asked to analyze data about flight delays by using SQL queries.

The second part of this assignment focuses on Airflow. You will start by initializing Airflow Docker containers. Next, you will be required to define a simple DAG that uses the PythonOperator Airflow Operator to return the value of a function. Finally, you will run your code inside the Airflow UI to ensure that your DAG works as expected.

Prior to beginning this assignment, review the submission instructions below to ensure that you collect the required screenshots as you progress through the assignment.

To complete this assignment, follow these steps:

## Part 1: PySpark

Create a new folder called bitnami. Open a command prompt window and navigate to the bitnami folder. Run the following curl command to download the docker-compose.yml file:

`curl https://raw.githubusercontent.com/bitnami/containers/main/bitnami/spark/docker-compose.yml -o docker-compose.yml`

Provide a screenshot to show that you correctly pulled the image and that the docker-compose.yaml file is present.

In a Terminal window, create containers by running the command below:

`docker-compose up`

Provide a screenshot of your Docker Desktop to show that you correctly pulled the containers.

Download the departuredelays.csv file on your machine. Perform a Docker copy command to copy this file to the bitnami_spark_1 container. 

`docker cp departuredelays.csv bitnami-spark-1:/departuredelays.csv`

Open the bitnami_spark_1 container to verify that you copied the file successfully. Provide a screenshot to show that you successfully copied the departuredelays.csv file to the bitnami_spark_1 container.

In the CLI window, type the correct command to open PySpark. `pyspark` Provide a screenshot to show that you successfully opened PySpark.

In the CLI window, type the correct command to import the correct package to start a PySpark session. 

`from pyspark.sql import SparkSession`

Provide a screenshot to show that you successfully imported the package.

In the CLI window, type the correct command to define a PySpark session named spark. Set the appName argument equal to Assignment19.3. 

spark = (SparkSession
    .builder
    .appName("Assignment19")
    .getOrCreate())

Provide a screenshot to show that you successfully defined the spark PySpark session.

In the CLI window, define a variable, assignment19_3_data, to hold the path to the departuredelays.csv file. 

`assignment19_3_data = "/departuredelays.csv"`

Provide a screenshot to show that you successfully defined the assignment19_3_data variable.

In the CLI window, define a dataframe, df, that will contain all of the entries in the departuredelays.csv file. 

df  = (spark.read.format("csv")
    .option("interSchema", "true")
    .option("header", "true")
    .load(assignment19_3_data))

Provide a screenshot to show that you successfully defined the df dataframe that contains all of the entries in the departuredelays.csv file.

In the CLI window, on the df dataframe use the createOrReplaceTempView method to create a view of the dataframe. Name the view assignment19_3_table. 

`df.createOrReplaceTempView("assignment19_3_table")`

Provide a screenshot to show that you successfully created a view of the assignment19_3_table dataframe.

In the CLI window, type an SQL query to select the first 15 flights from Philadelphia International Airport (PHL) to Dallas Fort Worth International Airport (DFW) that had a delay of greater than 150 minutes. 

`spark.sql("""SELECT * FROM assignment19_3_table WHERE origin = 'PHL' AND destination = 'DFW' AND delay > 150""").show(15)`

Provide a screenshot to show that you selected the correct entries from your data. Your data should display the first 15 flights from PHL to DFW that had a delay of greater than 150 minutes.

In the CLI window, type an SQL query to select the first 10 flights that have a distance of less than 200 miles. 

`spark.sql("""SELECT * FROM assignment19_3_table WHERE distance < 200""").show(10)`

Provide a screenshot to show that you selected the correct entries from your data. Your data should display the first 10 flights that have a distance of less than 200 miles. Ensure that the resulting table contains all of the columns in the original dataset.

In the CLI window, type an SQL query to select the first 10 flights that have a distance of greater than 600 miles. 

`spark.sql("""SELECT * FROM assignment19_3_table WHERE distance > 600""").show(10)`

Provide a screenshot to show that you selected the correct entries from your data. Your data should display the first 10 flights that have a distance greater than 600 miles. Ensure that the resulting table contains all of the columns in the original dataset.

## Part 2: Airflow

Create an empty folder called airflow_assignment on your local machine. Navigate to the airflow_assignment folder within a Terminal window and pull the Airflow file using the following command:

`curl https://airflow.apache.org/docs/apache-airflow/2.1.1/docker-compose.yaml -o docker-compose.yaml`

Provide a screenshot of your Terminal window response to show that you correctly pulled the Airflow file.

Open the generated docker-compose.yaml file using VS Code. Under "environment", set  the AIRFLOW__CORE__LOAD_EXAMPLES variable equal to false. Provide a screenshot to show the changed example value (AIRFLOW__CORE__LOAD_EXAMPLES set to false). 

In the Terminal window, run the `docker-compose up` command to start the Airflow Docker container. This creates the dags, logs, plugins folders. Open Docker Desktop and select the container to see all of the parts. Provide a screenshot to show that the Airflow Docker containers are running. 

In your web browser, navigate to http://localhost:8080/. Log in to Airflow using the default username and password: “airflow”. Provide a screenshot of your browser window to show that you have successfully logged in to Airflow.

Open VS Code and navigate to the dags folder inside the airflow_assignment folder. Inside this folder, create a new empty file called module19_assignment.py. Provide a screenshot to show that you created the module19_assignment.py file.

Copy the command below to import the required libraries for your DAG:

from datetime import timedelta, datetime
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from airflow.utils.dates import days_ago

Provide a screenshot to show that you correctly imported the required libraries.

In the module19_assignment.py file, add the following lines of code to define your DAG:

default_args = {
    'owner': 'XXX',
    'depends_on_past': False,
    'start_date': days_ago(2),
    'email': ['XXXX@YYY.com'],
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
}

Set the owner argument equal to your last name and replace the email field with your email address. Provide a screenshot to show that you set up your DAG correctly, including your last name and email address.

In the module19_assignment.py file, define a Python function, square(), that takes one positional argument, x, and returns that number squared. Provide a screenshot to show that you defined the square() function correctly.

Copy the code below into the module19_assignment.py file to define a DAG object:

dag = DAG(
    'python_square_operator',
    description = 'Squaring a number using Airflow',
    schedule_interval = “0 12 * * *”,
    Start_date = datetime(2017,3,20), catchup = False)

Provide a screenshot to show that you correctly defined the DAG object.

In the module19_assignment.py file define a Task, t1, that will return the square of the number 13. Declare this Task as a PythonOperator. Set the task_id parameter equal to square. Set the python_callable parameter equal to the Python function that you defined previously. Set the dag parameter to be equal to dag. Provide a screenshot to show that you defined the DAG Task correctly.

Navigate to http://localhost:8080/ to confirm that your DAG is configured correctly. Provide a screenshot of the Airflow UI to show that your DAG is configured correctly.

Start the DAG by toggling the switch to the left of its name. Select the DAG and open up the Graph View. Select the DAG again and open “logs”. Provide a screenshot of the log to show that the DAG ran successfully.