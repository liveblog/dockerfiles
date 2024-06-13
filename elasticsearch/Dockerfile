FROM openjdk:8-jre

ENV ES_VERSION=1.7.2

RUN wget -q https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-$ES_VERSION.tar.gz -O - | tar zxvf - \
    && mv /elasticsearch-$ES_VERSION /elasticsearch \
    && rm /elasticsearch/lib/sigar/*freebsd* && rm /elasticsearch/lib/sigar/*macosx* \
    && rm /elasticsearch/lib/sigar/*solaris* && rm /elasticsearch/lib/sigar/*winnt* \
    && rm /elasticsearch/bin/*.exe

EXPOSE 9200 9300

CMD ["elasticsearch/bin/elasticsearch"]
