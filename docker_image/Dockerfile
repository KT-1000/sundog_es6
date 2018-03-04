FROM ubuntu:16.04
RUN apt-get update -y
RUN apt-get upgrade -y

RUN echo 'Installing JDK'
RUN apt-get install -y default-jdk

RUN echo 'Installing wget and curl'
RUN apt-get install -y wget
RUN apt-get install -y curl

RUN echo 'Installing Elasticsearch 6'
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
RUN apt-get install -y apt-transport-https
RUN echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-6.x.list
RUN apt-get update && apt-get install elasticsearch

RUN echo 'Copying Custom Elasticsearch configuration'
COPY ./config/logging.yml /usr/share/elasticsearch/config/
COPY ./config/elasticsearch.yml /usr/share/elasticsearch/config/
COPY ./config/jvm.options /usr/share/elasticsearch/config/
COPY ./config/log4j2.properties /usr/share/elasticsearch/config/

COPY ./config/elasticsearch /etc/default/elasticsearch 
RUN chown -R root:elasticsearch /etc/default/elasticsearch

RUN sysctl -w vm.max_map_count=262144

RUN echo 'Configuring Elasticsearch user/group permissions'
WORKDIR /usr/share/elasticsearch
RUN set -ex && for path in data logs config config/scripts; do \
        mkdir -p "$path"; \
        chown -R elasticsearch:elasticsearch "$path"; \
    done

RUN echo 'Running Elasticsearch'
ENV ES_PATH_CONF=/usr/share/elasticsearch/
USER elasticsearch
ENV PATH=$PATH:/usr/share/elasticsearch/bin
CMD ["elasticsearch"]
EXPOSE 9200 9300
