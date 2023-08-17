# GSP430
## Run in cloudshell
```cmd
bq mk ecommerce
bq query --use_legacy_sql=false \
'#standardSQL
 CREATE OR REPLACE TABLE ecommerce.all_sessions_raw_dataprep
 OPTIONS(
   description="Raw data from analyst team to ingest into Cloud Dataprep"
 ) AS
 SELECT * FROM `data-to-insights.ecommerce.all_sessions_raw`
 WHERE date = "20170801";'
wget https://github.com/CodingWithHardik/files/raw/master/flow_Ecommerce_Analytics_Pipeline.zip
cloudshell download flow_Ecommerce_Analytics_Pipeline.zip
```
### Dataprep > Accept all conditions > flow > import flow > select the file 
### Remove first file from flow > Click + > import dataset > Bigquery > ecommerce > click + > import & add to flow > select
### Output > Run > Edit > Bigquery > GCP id > ecommerce > create new table > update > Run
