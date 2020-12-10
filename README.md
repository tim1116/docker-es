# docker-es
docker下安装elasticsearch

#### 安装
~~~
1:docker build -t myes .

2:docker run --name elasticsearch -p 9200:9200 -p 9300:9300  -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx128m" -v ./config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml -v ./data:/usr/share/elasticsearch/data -v ./plugins:/usr/share/elasticsearch/plugins -d myes
~~~



#### 参考资料
- https://hub.docker.com/_/elasticsearch docke官网
- https://github.com/dockerfile/elasticsearch