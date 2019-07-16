---
layout: post
title: How to run Oracle APEX in Docker container (Part I)
comments: true
---
This is part I: **Run Oracle Database and Oracle REST Data Service in container**

Oracle has an official [GitHub repository](https://github.com/oracle/docker-images) for running Oracle Database in Docker containers. I'll use a single instance Oracle Database Enterprise Edition version 18.3.0 as an example in this guide.
<!--more-->

### Get the dockerfile from GitHub
{% highlight bash %}
git clone https://github.com/oracle/docker-images.git
cd docker-images/OracleDatabase/SingleInstance
ls 18.3.0
./buildDockerImage.sh -v 18.3.0 -e
# -e means Enterprise Edition
{% endhighlight %}
For documentation, please check https://github.com/oracle/docker-images/tree/master/OracleDatabase/SingleInstance

### Build the docker image
Run following command in your terminal to build the image
{% highlight bash %}
docker run --name database -p 1521:1521 -p 5500:5500
            -e ORACLE_SID=ORA18C -e ORACLE_PDB=pdb1 -e ORACLE_PWD=oracle
            -e ORACLE_CHARACTERSET=AL32UTF8
            -v HOST_DIR:CONTAINER_DIR -d -it oracle/database:18.3.0-ee
{% endhighlight %}

#### Note
For now, I suggest use all **capital letters** for **ORACLE_SID**. Lower case SID become capitalized in this container and broke shell scripts.

### Take a look at your Oracle Database
{% highlight bash %}
docker exec -it database /bin/bash  # Enter the terminal inside the container
ps aux | grep pmon                  # List the database process
{% endhighlight %}

Now that the database is up and running, let's move on to Oracle REST Data Service (ORDS). The ORDS docker image was built on top of java docker image. Therefore we need to build the java image first.

### Oracle REST Data Service Docker Image
#### Download Java 8 Binaries
- Accept License and download [Java 8 binaries](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html)
- Put the downloaded **.tar.gz** file into docker-images/OracleJava/java-8

#### Build Java 8 Docker Image
{% highlight bash %}
cd docker-images/OracleJava/java-8
./build.sh
{% endhighlight %}

#### Build ORDS Docker Image
{% highlight bash %}
cd docker-images/OracleRestDataServices
./buildDockerImage.sh -i
# -i means ignore md5sum. I'm using ORDS 19.1 and its md5sum is not yet available in the repository.
# You can create your own md5sum file locally to ensure security.
{% endhighlight %}

