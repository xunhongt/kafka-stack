FROM confluentinc/cp-kafka:7.8.0

USER root

# Create directories for Ranger plugin
RUN mkdir -p /opt/kafka/libs/ranger-kafka-plugin-impl/conf

# Copy the Ranger plugin JARs and supporting files into the Kafka libs directory
COPY --chmod=644 ranger-2.7.0-kafka-plugin/lib/ranger-*.jar /usr/share/java/kafka/
COPY --chmod=644 ranger-2.7.0-kafka-plugin/lib/ranger-kafka-plugin-impl/ /usr/share/java/kafka/
COPY --chmod=644 ranger-2.7.0-kafka-plugin/conf/* /opt/kafka/libs/ranger-kafka-plugin-impl/conf/
# COPY --chmod=755 ranger-2.7.0-kafka-plugin/enable-kafka-plugin.sh /opt/kafka/libs/ranger-kafka-plugin-impl/enable-kafka-plugin.sh
# COPY --chmod=755 ranger-2.7.0-kafka-plugin/install.properties /opt/kafka/libs/ranger-kafka-plugin-impl/install.properties

# Ensure correct permissions for the directories and files
RUN find /opt/kafka/libs/ranger-kafka-plugin-impl/ -type d -exec chmod +x {} \;
RUN chmod -R 755 /opt/kafka/libs/
# RUN /opt/kafka/libs/ranger-kafka-plugin-impl/enable-kafka-plugin.sh /opt/kafka/libs/ranger-kafka-plugin-impl/install.properties
# Symlink the conf folder if needed by the specific plugin version (check your plugin's docs)
# RUN ln -s /opt/kafka/libs/ranger-kafka-plugin-impl/conf /opt/kafka/libs/ranger-kafka-plugin-impl/conf

# Switch back to the Kafka user (best practice for security)
USER 1000