# Apache Hadoop 2.7.1 Docker image

[![Docker Repository on Quay](https://quay.io/repository/cainelli/docker-hadoop/status "Docker Repository on Quay")](https://quay.io/repository/cainelli/docker-hadoop)


_Note1: This is a fork of [sequenceiq/hadoop-docker](https://github.com/sequenceiq/hadoop-docker) + Spark, Python 2.7.8 and Mongodb Connector._

_Note2: this is the master branch - for a particular Hadoop version always check the related branch_


# Build the image

If you'd like to try directly from the Dockerfile you can build the image as:

```
docker build  -t cainelli/hadoop-docker:2.7.1 .
```
# Pull the image

The image is also released as an official Docker image from Docker's automated build repository - you can always pull or refer the image when launching containers.

```
docker pull quay.io/cainelli/docker-hadoop
```

# Start a container

In order to use the Docker image you have just build or pulled use:

**Make sure that SELinux is disabled on the host. If you are using boot2docker you don't need to do anything.**

```
docker run -it quay.io/cainelli/docker-hadoop:latest /etc/bootstrap.sh -bash
```

## Pyspark + Mongo

```
/usr/local/spark/bin/pyspark --packages com.stratio.datasource:spark-mongodb_2.11:0.12.0
```

## Testing

You can run one of the stock examples:

```
cd $HADOOP_PREFIX
# run the mapreduce
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.1.jar grep input output 'dfs[a-z.]+'

# check the output
bin/hdfs dfs -cat output/*
```

## Hadoop native libraries, build, Bintray, etc

The Hadoop build process is no easy task - requires lots of libraries and their right version, protobuf, etc and takes some time - we have simplified all these, made the build and released a 64b version of Hadoop nativelibs on this [Bintray repo](https://bintray.com/sequenceiq/sequenceiq-bin/hadoop-native-64bit/2.7.0/view/files). Enjoy.
