ARG CERT_IMAGE
FROM $CERT_IMAGE as certs

FROM alpine:latest

ARG CERT_ENV
ARG CLIENT_NAME

WORKDIR /opt/jentrata

ADD cpa/ /opt/jentrata/cpa
ADD sql/ /docker-entrypoint-initdb.d

COPY conf/jentrata.conf /opt/jentrata/conf/jentrata.conf
COPY --from=certs /opt/jentrata/certs /opt/jentrata/certs

RUN sed -i s/CLIENT_NAME/$CLIENT_NAME/g /opt/jentrata/conf/jentrata.conf \
  && sed -i s/CERT_ENV/$CERT_ENV/g /opt/jentrata/conf/jentrata.conf

VOLUME /opt/jentrata/conf
VOLUME /opt/jentrata/certs
VOLUME /opt/jentrata/cpa
VOLUME /docker-entrypoint-initdb.d

CMD true
