FROM java:jdk

ONBUILD ARG COMPANYNAME
ONBUILD ARG PARTY_NAME=$COMPANYNAME
ONBUILD ARG PARTY_ID
ONBUILD ARG HOSTNAME
ONBUILD ARG YEAR
ONBUILD ARG CERT_ENV
ONBUILD ARG CERT_VALIDITY="732"
ONBUILD ARG KEY_PASS

WORKDIR /opt/jentrata/certs

ONBUILD RUN keytool -genkeypair -alias ${PARTY_NAME}-${CERT_ENV}-SSL \
  -keyalg RSA -keysize 2048 -sigalg SHA256withRSA \
  -dname "CN=${HOSTNAME}, OU=MULTI-ALLOWED, OU=${CERT_ENV}, OU=B2B ${YYYY}, OU=${PARTY_ID}, O=${COMPANYNAME}" \
  -validity 732 \
  -keystore "${COMPANYNAME}-${CERT_ENV}.jks" \
  -keypass $KEY_PASS \
  -storepass $KEY_PASS

ONBUILD RUN keytool -genkeypair -alias ${PARTY_NAME}-${CERT_ENV}-SIG \
  -keyalg RSA -keysize 2048 -sigalg SHA256withRSA \
  -dname "CN=${HOSTNAME}, OU=MULTI-ALLOWED, OU=${CERT_ENV}, OU=B2B ${YYYY}, OU=${PARTY_ID}, O=${COMPANYNAME}" \
  -validity 732 \
  -keystore "${COMPANYNAME}-${CERT_ENV}.jks" \
  -keypass $KEY_PASS \
  -storepass $KEY_PASS
