# What is this?
My initial attempt at learning the elastic stack via Udemy course: [Elasticsearch 6 and the Elastic Stack: In Depth and Hands On](https://www.udemy.com/elasticsearch-6-and-elastic-stack-in-depth-and-hands-on)

# How do I use it?
To run locally, first clone this repository and enter it:

<code>git clone https://github.com/katie-simmons/sundog_es6.git</code>

<code>cd sundog_es6</code>

In order to be able to complete the exercise(s) in each section, it is necessary to have an environment with the appropriate technologies.
While the course instructions specify creating an Ubuntu VM using VirtualBox and a downloaded ISO, we'll be using Docker containers instead. 
We'll still need VirtualBox, so download the appropriate version for your system here:

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Once downloaded, install VirtualBox. It will be used by docker-machine to create a machine on which the docker containers we'll need to do perform coursework will sit.
Each part of the elastic stack will be in its own docker container.

For example, if you cd into *docker_image* directory, you can build and run a docker container for elasticsearch by running the following commands:

<code>docker build -t elasticsearch .</code>

<code>docker run --rm -tid -p 9200:9200 elasticsearch</code>

## <a name="technologiesused"></a>Technologies Used
- [Elasticsearch](https://www.elastic.co/products/elasticsearch)
- [Logstash](https://www.elastic.co/products/logstash/)
- [Kibana](https://www.elastic.co/products/kibana)
- [Docker](https://www.docker.com/)

## <a name="features"></a>Features

*Current*

- [X] Dockerfile including elasticsearch 6 (and its JDK dependency)

*Future*

- [ ] Dockerfiles containing Kibana and Logstash
