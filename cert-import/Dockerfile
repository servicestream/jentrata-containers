ARG KEY_IMAGE
FROM $KEY_IMAGE as keys

FROM openjdk:jdk-alpine as certs

ARG CERT_URL
ARG CA_CERT_URL

ENV CERT_PATH=/opt/jentrata/certs
WORKDIR /opt/jentrata

COPY import-certs /bin/import-certs
COPY --from=keys $CERT_PATH/* $CERT_PATH/

RUN apk add --no-cache openssl \
  && . certs/.keystore \
  && wget -q $CERT_URL -O ${CERT_PATH}/${COMPANYNAME}-B2B-Certs-${CERT_ENV}-${YEAR}.zip \
  && wget -q $CA_CERT_URL -O ${CERT_PATH}/NBNCo-B2B-PublicKeyCertificates-${CERT_ENV}.zip

RUN import-certs

FROM scratch
ENV CERT_PATH=/opt/jentrata/certs
COPY --from=certs $CERT_PATH/ $CERT_PATH/
VOLUME $CERT_PATH/
