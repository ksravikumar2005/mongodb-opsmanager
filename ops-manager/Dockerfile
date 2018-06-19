FROM ubuntu:16.04

ENV OPS_MGR_VERSION=3.6.7.47243.20180606T1457Z-1

RUN apt-get update \
 && apt-get install -y wget vim curl libsasl2-2 libsnmp30 ca-certificates \
 && wget https://downloads.mongodb.com/on-prem-mms/deb/mongodb-mms_${OPS_MGR_VERSION}_x86_64.deb \
 && dpkg --install mongodb-mms_${OPS_MGR_VERSION}_x86_64.deb \
 && rm -f *.deb && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY default-conf-mms.properties /opt/mongodb/mms/conf/conf-mms.properties
COPY docker-entrypoint.sh /entrypoint.sh

VOLUME /etc/mongodb-mms /opt/mongodb/mms/conf /opt/mongodb/mms/logs

ENTRYPOINT ["/entrypoint.sh"]

CMD ["mongodb-mms"]
