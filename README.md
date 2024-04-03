# Basic-Structured-Api-Operations-in-Spark

created a spark session 
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName('abc').getOrCreate()
![image](https://github.com/srimanth496/Basic-Structured-Api-Operations-in-Spark/assets/84217751/5f8b3ca8-7af8-43bb-909f-3dc6dec8de6f)

create a data frame and  read file from the local system,
df = spark.read.format("json").load("C:/Users/srima/data/flight-data/json/2015-summary.json")
 print the schema .A schema defines the column names and types of a DataFrame
 df.printSchema()
 ![image](https://github.com/srimanth496/Basic-Structured-Api-Operations-in-Spark/assets/84217751/4e64e0b3-3332-43a5-80f9-29bf0f1ea0f4)
creating  a table from dataframe 
 df.createOrReplaceTempView("dfTable")
 extract two rows from that 
 Columns and Expressions : perform add columns and delete ,update columns
 import column function from pyspark    --
       from pyspark.sql.functions import col, column
. expression : performs set of logics in column to get output called expression
creating  row in pyspark - import row 
from pyspark.sql import Row
![image](https://github.com/srimanth496/Basic-Structured-Api-Operations-in-Spark/assets/84217751/c6a36999-90bb-4e1b-81af-71f8a937dcf9)

creating sql table in dataframe to perform sql operations in that table
df.createOrReplaceTempView("dfTable")

select expressions in dataframe :
display rows from the df by using select statements

df.select("DEST_COUNTRY_NAME").show(2)
df.select("DEST_COUNTRY_NAME", "ORIGIN_COUNTRY_NAME").show(2)

![image](https://github.com/srimanth496/Basic-Structured-Api-Operations-in-Spark/assets/84217751/b9ac3124-b3f0-4cfc-8f08-7e7124c37a9c)

. change column name 
df.select(expr("DEST_COUNTRY_NAME AS destination")).show(2)

By using lit function create column in a data frame and pass dummy values and change it when ever need it.

from pyspark.sql.functions import lit
df.select(expr("*"), lit(1).alias("One")).show(2)
![image](https://github.com/srimanth496/Basic-Structured-Api-Operations-in-Spark/assets/84217751/775a0ef4-d3f5-4e22-8631-06930173c51b)
perform add column and rename column and drop column 
rename : df.withColumnRenamed("DEST_COUNTRY_NAME", "dest").columns
add : df.select(expr("*"), lit(1).alias("One")).show(2)
delete :df.drop("ORIGIN_COUNTRY_NAME").columns

![image](https://github.com/srimanth496/Basic-Structured-Api-Operations-in-Spark/assets/84217751/e839dca6-ee07-4e8b-a146-d6d6a117b7f3)

. filter rows in data frame using two functions :
where
filter
df.filter(col("count") < 2).show(2) 






