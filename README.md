# elastic
Elastic Related help &amp; code
## Getting Started
### Cluster
#### Check Health og cluster
curl -XGET 'http://localhost:9200/_cluster/health'
#### Create Index
##### Plain Index
curl -X PUT 'localhost:9200/twitter?pretty'

