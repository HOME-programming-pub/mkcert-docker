# mkcert-docker
Generating self-signed certificates using [Docker](https://www.docker.com/) and [mkcert](https://github.com/FiloSottile/mkcert).

## Prerequisites
Linux with recent Git, Docker and Bash installed.

## Usage
```
git clone https://github.com/HOME-programming-pub/mkcert-docker.git
cd mkcert-docker
./gencerts.sh
```
This will generate client and root certificates as PEM files for the addresses defined in ``gencerts.sh``.

## Configuration
The addresses are defined in the script with the following defaults:
```
hosts="artemis.hs-merseburg.de\
       gitlab-artemis.hs-merseburg.de\
       localhost\
       127.0.0.1\
       ::1\
       *.artemis\
       artemis\
       gitlab-internal\
       gitlab-runner.internal"
```
This with generate the files
```
./gen/artemis.hs-merseburg.de+8-key.pem
./gen/artemis.hs-merseburg.de+8.pem
./gen/rootCA-key.pem
./gen/rootCA.pem
```
Adapt the addresses as needed by changing the value of the host variable. Note that the file names of the first two files will then change.

## Certificate Installation
To make the certifcates work, they need to be configured in your application (1) while the rootCA needs to be installed in a (local) CA trust store of your browser or OS (2). The step (2) may be ommitted, however, then the certificate will be untrusted.
