FROM elasticsearch:7.9.3

# These plugins are necessary to Liferay
RUN    ./bin/elasticsearch-plugin install analysis-icu \
    && ./bin/elasticsearch-plugin install analysis-kuromoji \
    && ./bin/elasticsearch-plugin install analysis-smartcn \
    && ./bin/elasticsearch-plugin install analysis-stempel

COPY elasticsearch.yml /usr/share/elasticsearch/config/
RUN chown -R elasticsearch:root /usr/share/elasticsearch/config/elasticsearch.yml

COPY liferay-inc-non_production-b8a3fe58-2b9d-4573-82ad-97b7c271822f-v5.json /usr/share/elasticsearch/license.json
RUN chown -R elasticsearch:root /usr/share/elasticsearch/license.json

COPY elasticsearch_startup.sh /usr/local/bin/elasticsearch_startup.sh
RUN chmod +x /usr/local/bin/elasticsearch_startup.sh


COPY jvm.options /usr/share/elasticsearch/config/
RUN chown -R elasticsearch:root /usr/share/elasticsearch/config/jvm.options

COPY limits.conf /etc/security
RUN chown -R elasticsearch:root /etc/security/limits.conf

CMD ["elasticsearch_startup.sh"]

