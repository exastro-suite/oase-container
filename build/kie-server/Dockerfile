FROM quay.io/kiegroup/kie-server:7.63.0.Final

# ENV KIE_SERVER_ID kie-server
ENV KIE_SERVER_LOCATION http://localhost:8080/kie-server/services/rest/server
ENV KIE_SERVER_USER kieserver
ENV KIE_SERVER_PWD kieserver1!
ENV KIE_SERVER_CONTROLLER_USER admin
ENV KIE_SERVER_CONTROLLER_PWD admin
ENV KIE_MAVEN_REPO http://localhost:8080/kie-wb/maven2
ENV KIE_MAVEN_REPO_USER admin
ENV KIE_MAVEN_REPO_PASSWORD admin
ENV JAVA_OPTS -Xms256m -Xmx1024m -Djava.net.preferIPv4Stack=true -Dfile.encoding=UTF-8

RUN mkdir -p $HOME/.m2
ADD ./files/etc/standalone-full-kie-server.xml $JBOSS_HOME/standalone/configuration/standalone-full-kie-server.xml
ADD ./files/etc/kie-server-users.properties $JBOSS_HOME/standalone/configuration/kie-server-users.properties
ADD ./files/etc/kie-server-roles.properties $JBOSS_HOME/standalone/configuration/kie-server-roles.properties
ADD ./files/etc/start_kie-server.sh $JBOSS_HOME/bin/start_kie-server.sh
ADD ./files/etc/settings.xml $JBOSS_HOME/../.m2/settings.xml

USER root
RUN chown jboss:jboss $JBOSS_HOME/standalone/configuration/standalone-full-kie-server.xml && \
chown jboss:jboss $JBOSS_HOME/standalone/configuration/kie-server-users.properties && \
chown jboss:jboss $JBOSS_HOME/standalone/configuration/kie-server-roles.properties && \
chown jboss:jboss $JBOSS_HOME/bin/start_kie-server.sh && \
chown jboss:jboss $JBOSS_HOME/../.m2/settings.xml

USER jboss

WORKDIR $JBOSS_HOME/bin/
CMD ["./start_kie-server.sh"]
