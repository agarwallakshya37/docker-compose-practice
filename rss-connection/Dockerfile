FROM wurstmeister/kafka:2.12-2.3.0

# Set up environment variables for Kafka and Connect
ENV KAFKA_BOOTSTRAP_SERVERS=kafka:9092
ENV CONNECT_REST_PORT=8083
ENV CONNECT_PLUGIN_PATH="/usr/share/kafka-connect-rss/plugins"

# Copy Kafka Connect configuration files
COPY connect-standalone.properties /opt/kafka/config
COPY rss-feed-connector.properties /opt/kafka/config

# Copy the necessary JAR files into the Kafka Connect plugin path
COPY ./plugins/ /usr/share/kafka-connect-rss/plugins

# we replace the start command creating a connector instead.
COPY start-kafka.sh /usr/bin/

# permissions
RUN chmod a+x /usr/bin/start-kafka.sh