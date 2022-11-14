# The idea
- Combinatation of apko and melange
- Turn the code into apk package
- Turn the apk package into container image
- Making sure that the final stage of your image composition is 100% visible to scan tools
- Having all of that upfront you can build an sbom, being confident that the results of your scan will be 10% accurate
- it also builds much smaller images
# how to build

## need apk-tools
apko has a dependency on apk-tools. If you're not running on Alpine Linux or another apk-based distribution, the quickest way to get apko running is to use the OCI Container (Docker) image:

docker pull cgr.dev/chainguard/apko:latest


## Create apko.yaml

## Run using apko image
docker run -v "$PWD":/work cgr.dev/chainguard/apko build images/alpine-base-rootless.yaml apko-alpine:edge apko-alpine.tar
docker run -v "$PWD":/work cgr.dev/chainguard/apko build images/nils.yaml apko-wolfii:test apko-wolfii.tar