### Jentrata SSL and Signing Private keys

This image is used to help generate private keys for SSL and for Signing for use with Jentrata

#### How To Use

* Create a Dockerfile like the one below
    ```Dockerfile
    FROM jentrata/generate-keys as keys
    #This triggers onbuild steps to generate private keys and stores them in a java keystore

    FROM scratch
    #this multi-stage step is optional just means the resulting container only contains the keystore
    COPY --from=keys /opt/jentrata/certs/*.jks /opt/jentrata/certs
    ```
* Build the container and push to your private repo
    ```bash
    $ docker build -t <my-private-repo>/jentrata/loopback-keys:2017-2018 \
      --build-arg COMPANYNAME="JENTRATA" \
      --build-arg PARTY_ID="MYPARTYID" \
      --build-arg HOSTNAME="MYHOSTNAME" \
      --build-arg YEAR="2017" \
      --build-arg CERT_ENV="TEST" \
      --build-arg CERT_VALIDITY="365" \
      --build-arg KEY_PASS="changeme" \
      .
    $ docker push <my-private-repo>/jentrata/loopback-keys:2017-2018
    ```
