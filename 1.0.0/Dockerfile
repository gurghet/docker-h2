FROM openjdk:10

# A fork of:
#  https://github.com/oscarfonts/docker-h2

LABEL maintainer="Andrea Passaglia <gurghet@gmail.com>"

ENV DOWNLOAD http://www.h2database.com/h2-2018-03-18.zip
ENV DATA_DIR /opt/h2-data
ENV WEB_PORT 81
ENV TCP_PORT 1521

RUN mkdir -p ${DATA_DIR} \
    && curl ${DOWNLOAD} -o h2.zip \
    && unzip h2.zip -d /opt/ \
    && rm h2.zip

COPY h2.server.properties /root/.h2.server.properties

EXPOSE ${WEB_PORT} ${TCP_PORT}

CMD java -cp /opt/h2/bin/h2*.jar org.h2.tools.Server \
 	-web -webAllowOthers -webPort ${WEB_PORT} \
 	-tcp -tcpAllowOthers -tcpPort ${TCP_PORT} \
 	-baseDir ${DATA_DIR}
