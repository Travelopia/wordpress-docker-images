FROM openjdk:7

ENV SOLR_PORT 8983

WORKDIR /opt

RUN curl -s https://archive.apache.org/dist/lucene/solr/3.6.2/apache-solr-3.6.2.tgz > apache-solr.tgz && \
    tar xfvz apache-solr.tgz && \
    rm apache-solr.tgz

WORKDIR /opt/apache-solr-3.6.2/example

CMD java -Djetty.port=${SOLR_PORT} -jar start.jar