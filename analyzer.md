# Analyzer Info
###### Analyzer output 
curl -X POST "http://localhost:9200/_analyze " -H 'Content-Type: application/json' -d'
{
   "analyzer": "standard",
   "text": "Today's weather is beautiful"
}
'

