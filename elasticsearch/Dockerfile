FROM elasticsearch:7.9.3

# These plugins are necessary to Liferay
RUN    ./bin/elasticsearch-plugin install analysis-icu \
    && ./bin/elasticsearch-plugin install analysis-kuromoji \
    && ./bin/elasticsearch-plugin install analysis-smartcn \
    && ./bin/elasticsearch-plugin install analysis-stempel

COPY --chown=elasticsearch:elasticsearch elasticsearch.yml /usr/share/elasticsearch/config
COPY --chown=elasticsearch:elasticsearch jvm.options /usr/share/elasticsearch/config
COPY --chown=elasticsearch:elasticsearch limits.conf /etc/security