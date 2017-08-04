### Jentrata SSL and Signing Private keys with generate of Certifcate Signing Request

This image is used to help generate private keys for SSL and for Signing along with CSRs for use with Jentrata

#### How To Use

* Clone this repo and build the container and push to your private repo
    ```bash
    $ docker build -t <my-private-repo>/jentrata/loopback-keys:2017-2018 \
      --build-arg COMPANYNAME="JENTRATA" \
      --build-arg PARTY_ID="MYPARTYID" \
      --build-arg YEAR="2017" \
      --build-arg CERT_HOSTNAME="MYHOSTNAME" \
      --build-arg CERT_ENV="TEST" \
      --build-arg CERT_VALIDITY="365" \
      --build-arg KEY_PASS="changeme" \
      .
    $ docker push <my-private-repo>/jentrata/loopback-keys:2017-2018
    ```
