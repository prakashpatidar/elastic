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
##### Create Index with Mapping
curl -X PUT "http://localhost:9200/test?pretty" -H 'Content-Type: application/json' -d'
{
    "settings" : {
        "number_of_shards" : 1
    },
    "mappings" : {
        "properties" : {
            "field1" : { "type" : "text" }
        }
    }
}
'
###### Get Index Mapping
curl -X GET "http://localhost:9200/test/_mapping?pretty"
###### Edit Mapping
curl -X PUT "http://localhost:9200/test/_mapping?pretty" -H 'Content-Type: application/json' -d'
{
  "properties": {
    "field2": {
      "type": "integer"
    }
  }
}
'
###### Edit Mapping , add non indexable field
curl -X PUT "http://localhost:9200/test/_mapping?pretty" -H 'Content-Type: application/json' -d'
{
  "properties": {
    "field3": {
      "type": "integer",
      "index": false
    }
  }
}
'
###### View Mapping of specific field in index
curl -X GET "http://localhost:9200/test/_mapping/field/field3?pretty"

###### Edit Index Setting

curl -X PUT "http://localhost:9200/test/_settings?pretty" -H 'Content-Type: application/json' -d'
{
    "index" : {
        "number_of_replicas" : 2
    }
}
'
###### Create Index with Analyzer in field
curl -X PUT "http://localhost:9200/test?pretty" -H 'Content-Type: application/json' -d'
{
  "settings": {
    "index": {
      "number_of_shards": 1,
      "number_of_replicas": 2
    },
    "analysis": {
      "analyzer": {
        "my_analyzer": {
          "type": "custom",
          "tokenizer": "standard",
          "filter": [
            "lowercase"
          ]
        },
        "my_stop_analyzer": {
          "type": "custom",
          "tokenizer": "standard",
          "filter": [
            "lowercase",
            "english_stop"
          ]
        }
      },
      "filter": {
        "english_stop": {
          "type": "stop",
          "stopwords": "_english_"
        }
      }
    }
  },
  "mappings": {
    "properties": {
      "name": {
        "type": "text"
      },
      "title": {
        "type": "text",
        "analyzer": "my_analyzer",
        "search_analyzer": "my_stop_analyzer",
        "search_quote_analyzer": "my_analyzer"
      }
    }
  }
}
'

