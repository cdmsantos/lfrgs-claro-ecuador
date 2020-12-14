FROM elasticsearch:7.9.3

# These plugins are necessary to Liferay
RUN    ./bin/elasticsearch-plugin install analysis-icu \
    && ./bin/elasticsearch-plugin install analysis-kuromoji \
    && ./bin/elasticsearch-plugin install analysis-smartcn \
    && ./bin/elasticsearch-plugin install analysis-stempel

COPY elasticsearch.yml /usr/share/elasticsearch/config
RUN chown -R elasticsearch:root /usr/share/elasticsearch/config/elasticsearch.yml

COPY jvm.options /usr/share/elasticsearch/config
RUN chown -R elasticsearch:root /usr/share/elasticsearch/config/jvm.options

COPY limits.conf /etc/security
RUN chown -R root:root /etc/security/limits.conf
