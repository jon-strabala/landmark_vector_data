# landmark_vector_data

A set of 4495 Vector embeddings for the Couchbase collection `travel-sample.inventory.landmark`

## The embedding Vectors

This area contains an update for `travel-sample.inventory.landmark` data with OpenAI vectors as follows:
```
doc.embedding = doc.name + " " + doc.content
```
Each vector was made via the text-embedding-ada-002-v2 embedding model.  This data set only adds two fields to the original data `emebedding`

## To load into a Couchbase OnPrem server 

Steps:
* Download `landmark_all_lines.json.gz`  from this repository.
* Uncompress the above files.
```
gunzip landmark_all_lines.json.gz
```
* load the travel-sample data set
```
In the UI select Settings
Sample Buckets
Check [X] travel-sample
Hit the `Load Sample Data` button
```
* Import the `landmark_all_lines.1.json` and landmark_all_lines.2.json` data
```
cbimport json -c couchbase://$CB_HOSTNAME  \
        -u $CB_USERNAME -p $CB_PASSWORD -b travel-sample -f lines -d file://./landmark_all_lines.json \
        --scope-collection-exp inventory.landmark -g landmark_%id%
```

## A sample data item KEY landmark_10019

```
{
  "title": "Gillingham (Kent)",
  "name": "Royal Engineers Museum",
  "alt": null,
  "address": "Prince Arthur Road, ME4 4UG",
  "directions": null,
  "phone": "+44 1634 822839",
  "tollfree": null,
  "email": null,
  "url": "http://www.remuseum.org.uk",
  "hours": "Tues - Fri 9.00am to 5.00pm, Sat - Sun 11.30am - 5.00pm",
  "image": null,
  "price": null,
  "content": "Adult - \u00a36.99 for an Adult ticket that allows you to come back for further visits within a year (children's and concessionary tickets also available). Museum on military engineering and the history of the British Empire. A quite extensive collection that takes about half a day to see. Of most interest to fans of British and military history or civil engineering. The outside collection of tank mounted bridges etc can be seen for free. There is also an extensive series of themed special event weekends, admission to which is included in the cost of the annual ticket.",
  "geo": {
    "accuracy": "RANGE_INTERPOLATED",
    "lat": 51.39184,
    "lon": 0.53616
  },
  "activity": "see",
  "type": "landmark",
  "id": 10019,
  "country": "United Kingdom",
  "city": "Gillingham",
  "state": null,
  "embedding_crc": "64db70ad634a6ad4",
  "embedding": [0.0022478399332612753, ... 1535 items removed ... ]
}
```
