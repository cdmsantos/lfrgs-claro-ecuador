FROM liferay/dxp:7.2.10-dxp-9

EXPOSE 8080 8000 11311

ENV LIFERAY_HOME /opt/liferay
ENV TOMCAT_HOME $LIFERAY_HOME/tomcat

USER root

# Add Liferay license
COPY license/* $LIFERAY_HOME/osgi/modules

# Add Liferay ES Connector
COPY deploy/* $LIFERAY_HOME/osgi/marketplace

# Add OSGi configs 
COPY osgi/configs/* $LIFERAY_HOME/osgi/configs/

# Configure database conection (with permissions to liferay user)
COPY tomcat/conf/Catalina/localhost/* $TOMCAT_HOME/conf/Catalina/localhost/

# Add database libs
COPY tomcat/lib/ext/* $TOMCAT_HOME/lib/ext/

# Configure Liferay
COPY properties/* $LIFERAY_HOME/

# Give permission to all files to liferay user 
RUN chown -R liferay:liferay $LIFERAY_HOME/*

USER liferay

WORKDIR $LIFERAY_HOME