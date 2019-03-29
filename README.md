# spark-janusgraph-docker

> Spark Docker containers which already contain the Janusgraph jars required to use them for OLAP queries with Janus.

For spark to work with Janusgraph matching the exact versions is very important. These images are designed for exactly the versions mentioned and can of course be extended to contain other version as well.

These Dockerfiles are based on the images from [Big Data Europe](https://github.com/big-data-europe/docker-spark) which fortunately contain plenty of different versions. We extend this images by adding the jars required for janusgraph to work with spark for both the masters and workers.

## Versions

The images are built and tagged according to the version of JanusGraph and Spark used. Builds are triggered automatically on DockerHub based on tags. 

To create new images, simply create a new git tag. Naming format: [SPARK_VERSION]-janus-[JANUS_VERSION]
