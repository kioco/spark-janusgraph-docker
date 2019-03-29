FROM bde2020/spark-worker:1.6.3-nohadoop-java8

# download janusgraph to include jars
RUN apt-get update && apt-get install -y unzip wget
RUN mkdir /janus && cd /janus && wget https://github.com/JanusGraph/janusgraph/releases/download/v0.2.2/janusgraph-0.2.2-hadoop2.zip
RUN cd /janus && unzip janusgraph-0.2.2-hadoop2.zip
# the target path here must match the janusgraph config "/opt/lib/janusgraph"
# is the default suggested in the janus docs
RUN mkdir -p /opt/lib/janusgraph && cp -r /janus/janusgraph-0.2.2-hadoop2/lib/* /opt/lib/janusgraph/
# let's clean up again, we don't need most of the 270MB archive
RUN rm -rf /janus

# set reasonable defaults for all startup args, so it's possible to start the
# container without having to specify additional config
ENV SPARK_MASTER="spark://spark-master:7077"
ENV SPARK_WORKER_WEBUI_PORT=8080

ENTRYPOINT ["/bin/sh", "-c"]

CMD ["/spark/sbin/../bin/spark-class org.apache.spark.deploy.worker.Worker --webui-port $SPARK_WORKER_WEBUI_PORT $SPARK_MASTER" ]
