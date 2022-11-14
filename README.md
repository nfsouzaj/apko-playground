# how to build

## need apk-tools
apko has a dependency on apk-tools. If you're not running on Alpine Linux or another apk-based distribution, the quickest way to get apko running is to use the OCI Container (Docker) image:

docker pull cgr.dev/chainguard/apko:latest


## Create apko.yaml

## Run using apko image
docker run -v "$PWD":/work cgr.dev/chainguard/apko build examples/alpine-base.yaml apko-alpine:edge apko-alpine.tar

docker run -v "$PWD":/work cgr.dev/chainguard/apko build wolfi-base/apko.yaml apko-wolfi:test apko-wolfi.tar\
docker run -v "$PWD":/work cgr.dev/chainguard/apko build image/nils.yaml apko-wolfii:test apko-wolfii.tar