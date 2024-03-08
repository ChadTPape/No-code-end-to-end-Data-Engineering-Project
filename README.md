# No code end to end Data Engineering Project


![1](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/72587afc-2e66-4581-bb25-a39acb439693)


This is an end to end data engineering project and pipeline in AWS to deepen my understanding of cloud concepts and how each service works in the Data Engineering pipeline. Here is the dataset which I used https://www.kaggle.com/datasets/tonygordonjr/spotify-dataset-2023

Dataset:

spotify_tracks_data_2023.csv
spotify-albums_data_2023.csv
spotify_artist_data_2023.csv
Among the 5 files given I downloaded only albums ,artist and track file .

The project utilizes the following AWS services:

AWS Crawler
AWS S3 (Simple Storage Service)
AWS Glue
Amazon Athena

Create S3 Buckets:

![2](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/51ab699d-c6ba-434b-8996-43dc6e6eb9a0)


Staging - I created a staging bucket in order to load my spotify dataset. The data is then stored in the csv format, before uploading it to S3 I removed some useless columns from all three tables. I then uploaded the three files to S3.

![3](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/1f940185-8311-4ae1-8cff-35ab5992e267)



Data Lake - I created the empty data warehouse bucket in order to store my transformed data after applying the glue operations on the respective tables.

Glue ETL

Perform the various operations in Glue tables like joining different tables by common columns or dropping the unnecssary fields, eg: if artist_id column is repeated twice after join I will drop one.

After performing all the operations and forming the visual ETL pipeline I ran, monitored and stored the result in the target S3 bucket which is named datawarehouse in parquet format.


![4](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/e1498803-7bcc-4bbd-9ffb-435f07f3125c)



AWS Glue will automatically form the spark code for the above visual pipeline as shown below hence no coding is required from my end. I can check the spark code to better understand my data and operations.


![5](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/310c6573-4d74-4aae-bf11-d258b1204e4f)



The datawarehouse folder which is formed in S3 stores the parquet format file after the job is run successfully.


![6](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/ed8d5959-f7f0-45b6-a2e7-1f315f677ff2)



GLUE CRAWLER

AWS Glue crawler to create a catalog and a database containing metadata about my data sources, making it easier to work with them for various data processing tasks.


![7](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/119caaca-3afb-4351-8b83-4963130ad7ce)



If required we can also change the type of column eg: from string to int using Edit schema JSON option available in AWS crawler.


![8](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/bf52df1a-ea5e-4712-9b88-025f16c6f978)



AWS ATHENA

After the schema is formed I used AWS Athena and setup the query editor to perform the sql operations on my spotify data as shown below, it will show the query output after RUN button is pressed. To better understand the data and perform query operations we can also create a separate folder in S3 for AWS Athena to store the output of specific query in separate file.


![9](https://github.com/ChadTPape/No-code-end-to-end-Data-Engineering-Project/assets/131377285/123600c7-95f5-4aa2-a0a1-daeefd48de32)
