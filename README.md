# elastic
Elastic Related help &amp; code
## Getting Started
### Cluster
#### Check Health og cluster
curl -X GET 'http://localhost:9200/_cluster/health'
#### Index DDL API
##### Create Plain Index
curl -X PUT 'http://localhost:9200/cdr?pretty'
##### Drop Index
curl -X DELETE "localhost:9200/twitter?pretty"



