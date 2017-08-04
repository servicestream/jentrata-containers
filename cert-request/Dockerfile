FROM jentrata/generate-keys as keys
#This triggers onbuild steps to generate private keys and stores them in a java keystore
FROM scratch
ENV CERT_PATH=/opt/jentrata/certs
COPY --from=keys $CERT_PATH/* $CERT_PATH/
