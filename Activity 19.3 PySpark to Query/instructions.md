In this activity, you will use the Bitnami containers that you created in Video 19.3, the data that you loaded in Video 19.4, and PySpark to write SQL queries. The goal of this activity is for you to gain further insight into your data about the delays between flights across the United States.

Note that before you begin this activity, you will need to successfully complete all of the steps demonstrated in the previous videos.

Prior to beginning this activity, review the submission instructions below to ensure that you collect the required screenshots as you progress through the activity.

To complete this activity, follow these steps:

Open Docker Desktop on your machine. Provide a screenshot to show that you have the Bitnami containers up and running.

Open the CLI for the bitnami_spark_1 container. Navigate to the root folder. Provide a screenshot to show that the departuredelays.csv file is in the root folder.

In the CLI window, type the correct command to open PySpark. 
`pyspark`
Provide a screenshot to show that you successfully opened PySpark.

In the CLI window, type the correct command to import the correct package to start a PySpark session. 

`from pyspark.sql import SparkSession`

Provide a screenshot to show that you successfully started a PySpark session.

In the CLI window, type the correct command to define a PySpark session named spark. Set the appName argument equal to Activity19.3. 

#spark session
spark = (SparkSession
    .builder
    .appName("Activity19.3")
    .getOrCreate())

Provide a screenshot to show that you successfully defined the spark PySpark session.

In the CLI window, define a variable, activity19_3_data, to hold the path to the departuredelays.csv file. 

`activity19_3_data = "/departuredelays.csv"`

Provide a screenshot to show that you successfully defined the activity19_3_data variable.

In the CLI window, define a dataframe, df, that will contain all of the entries in the departuredelays.csv file. 

df  = (spark.read.format("csv")
    .option("interSchema", "true")
    .option("header", "true")
    .load(activity19_3_data))

Provide a screenshot to show that you successfully defined the df dataframe.

In the CLI window, on the df dataframe, use the createOrReplaceTempView method to create a view of the dataframe. Name the view activity19_3_table. 

`df.createOrReplaceTempView("activity19_3_table")`

Provide a screenshot to show that you successfully created a view of the dataframe that is named activity19_3_table.

In the CLI window, type an SQL query to select the first 10 flights from John F. Kennedy International Airport (JKF) to Seattle-Tacoma International Airport (SEA) that had a delay of greater than 90 minutes.

`spark.sql("""SELECT * FROM activity19_3_table WHERE delay > 90 AND origin = 'JFK' AND destination = 'SEA'""").show(10)`

Provide a screenshot to show that you selected the correct entries from your data. Your data should display the first 10 flights from JFK to SEA that had a delay of greater than 90 minutes.

In the CLI window, type an SQL query to select the first five flights from San Francisco International Airport (SFO) to Miami International Airport (MIA) that had a delay of less than 60 minutes. 

`spark.sql("""SELECT * FROM activity19_3_table WHERE delay < 60 AND origin = 'SFO' AND destination = 'MIA'""").show(5)`

Provide a screenshot to show that you selected the correct entries from your data. Your data should display the first five flights from SFO to MIA that had a delay of less than 60 minutes.