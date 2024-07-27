# docker-es
docker下安装elasticsearch

#### 安装elasticsearch
~~~
1:docker build -t myes .

2:docker network create es 

3:docker run --name elasticsearch -p 9200:9200 -p 9300:9300  -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx128m" -v ./config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml -v ./data:/usr/share/elasticsearch/data -v ./plugins:/usr/share/elasticsearch/plugins -d myes (挂载目录)

3:docker run --name elasticsearch --net es -p 9200:9200 -p 9300:9300  -e "discovery.type=single-node"  -d myes

4:sudo docker restart elasticsearch (重启)

~~~

#### 安装elasticsearch+Kibana (推荐)
~~~
1:docker build -t myes .

2:docker network create es 

3:docker run --name elasticsearch --net es -p 9200:9200 -p 9300:9300  -e "discovery.type=single-node"  -d myes

4:docker pull kibana:7.16.1 （保证版本一样）

5:docker run -d --name kibana -e "I18N_LOCALE=zh-CN" --net es -p 5601:5601 kibana:7.16.1
~~~



#### 测试

http://<host>:9200  查看是否安装成功 针对es

http://<host>:5601  查看是否安装成功 针对Kibana

#### 参考资料
- https://hub.docker.com/_/elasticsearch docke官网
- https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html (推荐)
- https://www.elastic.co/guide/cn/elasticsearch/php/current/index.html  php api
- https://github.com/elastic/go-elasticsearch go api
- ....