FROM ubuntu:16.04
RUN apt-get update -y
RUN apt-get upgrade -y

RUN echo 'Installing JDK'
RUN apt-get install -y default-jdk

RUN echo 'Installing Elasticsearch 6'
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
RUN apt-get install -y apt-transport-https
RUN echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
RUN sudo apt-get update && sudo apt-get install elasticsearch

RUN echo 'Copying Custom Elasticsearch configuration'
COPY logging.yml /usr/share/elasticsearch/config/
COPY elasticsearch.yml /usr/share/elasticsearch/config/

RUN echo 'Configuring Elasticsearch user/group permissions'
WORKDIR /usr/share/elasticsearch
RUN set -ex && for path in data logs config config/scripts; do \
        mkdir -p "$path"; \
        chown -R elasticsearch:elasticsearch "$path"; \
    done

RUN echo 'Running Elasticsearch'
USER elasticsearch
ENV PATH=$PATH:/usr/share/elasticsearch/bin
CMD ["elasticsearch"]
EXPOSE 9200 9300
