FROM liferay/dxp:7.2.10-dxp-9

EXPOSE 8080 8000 11311

ENV LIFERAY_HOME /opt/liferay
ENV TOMCAT_HOME $LIFERAY_HOME/tomcat

USER root

# Add Liferay license (with permissions to liferay user)
COPY deploy/* $LIFERAY_HOME/osgi/modules

# Add OSGi configs (with permissions to liferay user)
#COPY osgi/configs/* $LIFERAY_HOME/osgi/configs

# Configure database conection (with permissions to liferay user)
COPY tomcat/conf/Catalina/localhost/* $TOMCAT_HOME/conf/Catalina/localhost/

# Add database libs (mysql and oracle) (with permissions to liferay user)
COPY tomcat/lib/ext/* $TOMCAT_HOME/lib/ext/

# Configure Liferay (with permissions to liferay user)
COPY properties/* $LIFERAY_HOME/
RUN chown -R liferay:liferay $LIFERAY_HOME/*

RUN mkdir /opt/liferay/data/document_library 

RUN chown -R liferay:liferay $LIFERAY_HOME/*

USER liferay

WORKDIR $LIFERAY_HOME