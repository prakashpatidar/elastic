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
##### Create Index for n shard and r replicas
curl -X PUT "http://localhost:9200/cdr?pretty" -H 'Content-Type: application/json' -d'
{
    "settings" : {
        "index" : {
            "number_of_shards" : 3, 
            "number_of_replicas" : 2 
        }
    }
}
'
##### List Indexes
curl -X GET "http://localhost:9200/_cat/indices/*?v&s=index&pretty"



