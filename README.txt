The original dataset and the cleaned dataset both locate in HDFS:

Original: hdfs://nyu-dataproc-m/user/yw4359_nyu_edu/hw10/SSE_A_Stock.csv
Cleaned: hdfs://nyu-dataproc-m/user/yw4359_nyu_edu/hw10/result/part-r-00000


Please follow below steps in order:

HDFS:


- upload the java files
- run following commands:

- javac -classpath `yarn classpath` -d . CleanMapper.java
- javac -classpath `yarn classpath` -d . CleanReducer.java
- javac -classpath `yarn classpath`:. -d . Clean.java
- jar -cvf Cleann.jar *.class
- hadoop jar Cleann.jar Clean hw10/SSE_A_Stock.csv  hw10/result

(The cleaned dataset is in hw10/result)



Hive:

1. create external table if not exists stock(stockId INT, company STRING,
industry_code_A STRING, industry_code_C STRING, Premium_price
DOUBLE,ipo_price DOUBLE, share_issued INT, trading_month
INT,closing_price DOUBLE, marketvalue_share DOUBLE) ROW FORMAT
DELIMITED FIELDS TERMINATED BY "," STORED AS TEXTFILE
LOCATION "hdfs://nyu-dataproc-m/user/yw4359_nyu_edu/hw10/result";

	creates a Hive table based on the dataset located in "hdfs://nyu-dataproc-m/user/yw4359_nyu_edu/hw10/result" 


After completing above steps, run the codes in Code.txt in order

