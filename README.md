# What is this?
A way for [Katie Simmons](https://github.com/katie-simmons) and [Nate Rock](https://github.com/rockhowse) to learn 
the elastic stack via Frank Kane's Udemy course [Elasticsearch 6 and the Elastic Stack: In Depth and Hands On](https://www.udemy.com/elasticsearch-6-and-elastic-stack-in-depth-and-hands-on).

Dockerization based on elastic.co's excellent [elasticsearch docker tutorial](https://www.elastic.co/blog/how-to-make-a-dockerfile-for-elasticsearch).

# How do I use it?
If you're taking the same course and want a self-contained setup to do all the coursework, first pop open a terminal and
enter the following commands to get a local copy of this repo and enter it:

<code>git clone https://github.com/katie-simmons/sundog_es6.git</code>

<code>cd sundog_es6</code>

To complete the exercises in each section, it is necessary to have an environment with the appropriate technologies.
While the course instructions specify creating an Ubuntu VM using VirtualBox and a downloaded ISO, we'll be using Docker 
containers instead. We'll still need VirtualBox though, so download the appropriate version for your system here:

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Once downloaded, install VirtualBox. It will be used by docker-machine to create a place for the docker containers 
we'll need to do perform coursework to sit. 

Each part of the elastic stack will be in its own docker container. For example, if you cd into the *docker_image* 
directory, you can build and run a docker container for elasticsearch via these commands:

<code>docker build -t elasticsearch .</code>

<code>docker run --rm -tid -p 9200:9200 elasticsearch</code>

Now you have a docker container named 'elasticsearch' running elasticsearch6, which can be used for future exercises.


## <a name="technologiesused"></a>Technologies Used
- [Elasticsearch](https://www.elastic.co/products/elasticsearch)
- [Logstash](https://www.elastic.co/products/logstash/)
- [Kibana](https://www.elastic.co/products/kibana)
- [Docker](https://www.docker.com/)

## <a name="features"></a>TODO
- [X] Dockerfile including elasticsearch 6 (and its JDK dependency)
- [ ] Dockerfiles containing Kibana and Logstash
- [ ] Docker-compose
- [ ] Can connect to docker image and run setup_shakespeare script successfully 

# Coursework
## Section 1
To try out the docker container and get a taste of elasticsearch6, let's run a script in the docker container to
install the collected works of William Shakespeare and query for the phrase "to be or not to be":

<code>docker exec elasticsearch ./section-1/setup_shakespeare.sh</code>

You should see the following JSON returned in your terminal:

<code>
{}
</code>
