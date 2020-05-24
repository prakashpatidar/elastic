# Analyzer Info
###### Analyzer output 
curl -X POST "http://localhost:9200/_analyze" -H 'Content-Type: application/json' -d'
{
   "analyzer": "standard",
   "text": "Today's weather is beautiful"
}
'
###### Configuring the Standard analyzer
curl -X PUT "http://localhost:9200/index_4_analysis" -H 'Content-Type: application/json' -d'
{
   "settings": {
      "analysis": {
         "analyzer": {
            "my_english_analyzer": {
               "type": "standard",
               "max_token_length": 5,
               "stopwords": "_english_"
            }
         }
      }
   }
}
'
