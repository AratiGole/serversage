FROM tomcat:9.0

# Install the OpenTelemetry Java Agent
ADD opentelemetry-javaagent.jar /usr/local/tomcat/opentelemetry-javaagent.jar

# Copy your sample .war application
COPY sample.war /usr/local/tomcat/webapps/
COPY aina.war /usr/local/tomcat/webapps/
# COPY sample_old.war /usr/local/tomcat/webapps/

# Set environment variables for OpenTelemetry
ENV JAVA_OPTS="-javaagent:/usr/local/tomcat/opentelemetry-javaagent.jar \
-Dotel.exporter.otlp.endpoint=http://host.docker.internal:4318 \
-Dotel.service.name=sample"

# Expose port
EXPOSE 8080

# Start Tomcat
CMD ["catalina.sh", "run"]
