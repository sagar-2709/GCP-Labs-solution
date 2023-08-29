# RUN IN CLOUDSHELL
```cmd
export BUCKET_NAME=
```
```cmd
export DATASET_NAME=
```
```cmd
export TABLE_NAME=
```
```cmd
export TOPIC_NAME=
```

```cmd
gsutil mb gs://$BUCKET_NAME

bq mk $DATASET_NAME

bq mk --table \
$DEVSHEL_PROJECT_ID:$DATASET_NAME.$TABLE_NAME \
data:string

gcloud pubsub topics create $TOPIC_NAME

gcloud pubsub subscriptions create $TOPIC_NAME-sub --topic=$TOPIC_NAME
```
