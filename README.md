# es-docker

### 1. Build server by docker

-   Pulling the image: docker pull docker.elastic.co/elasticsearch/elasticsearch:7.17.18

-   Starting a single node cluster with Docker: docker run -p 127.0.0.1:9200:9200 -p 127.0.0.1:9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.17.18

-   create docker-compose.yml file

-   run: docker-compose up

# docs: https://www.elastic.co/guide/en/elasticsearch/reference/7.17/docker.html

### 2. How to create Index in Elasticsearch

**We are use ES throught RestAPIs: GET, POST, PUT, DELETE**

-   Add new index: PUT/{index_name}
-   Add settings in request body: {
    "settings" : {
    "index" : {
    "number_of_shards" : 3,
    "number_of_replicas" : 2
    }
    }
    }
-   Add mappings for index fields: {
    "mappings" : {
    "properties" : {
    "name" : { "type" : "text" }
    }
    }
    }

### 3. How to query

-   GET /\_search?q={keyword} => all fields
-   GET /\_search?q={field_name}:{keyword} => by field name

**or request body**
{
"query": {
"multi_match" : {
"query" : {keyword},
"fields" : ["_all"]
}
}
}

# docs: https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl.html
