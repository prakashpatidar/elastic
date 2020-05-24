# elastic
Elastic Related help &amp; code
## Getting Started
### Cluster
#### Check Health og cluster
curl -X GET 'http://localhost:9200/_cluster/health'
#### Create Index
##### Plain Index
curl -X PUT 'http://localhost:9200/cdr?pretty'


