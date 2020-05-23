ElasticSearch

https://kb.objectrocket.com/elasticsearch/how-to-get-elasticsearch-documents-using-golang-448
using go-elasticsearchs

https://www.freecodecamp.org/news/go-elasticsearch/

docker pull docker.elastic.co/elasticsearch/elasticsearch:7.6.2

docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.6.2


GET localhost:9200
PUT localhost/9200/students

POST localhost:9200/students/doc
{
	"name":"Alice",
	"age":17,
	"average_score":81.1
}


POST /students/_bulk
{ "index":{"_index": "students" } }
{ "name":"john doe","age":18, "average_score":77.7 }
{ "index":{"_index": "students" } }
{ "name":"bob","age":16, "average_score":65.5 }
{ "index":{"_index": "students" } }
{ "name":"mary doe","age":18, "average_score":97.7 }
{ "index":{"_index": "students" } }
{ "name":"eve","age":15, "average_score":98.9 }



 POST localhost:9200/_search
{
    "query" : {
        "match" : { "name" : "doe" }
    }
}



