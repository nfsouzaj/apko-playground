# The idea
- Combinatation of apko and melange
- Turn the code into apk package
- Turn the apk package into container image
- Making sure that the final stage of your image composition is 100% visible to scan tools as scanners can only see what is installed via package manager
- Having all of that upfront you can build an sbom, being confident that the results of your scan will be 100% accurate
- it also builds much smaller images

# Why not distroless 
- Easier to handle apko in detriment of bazel
# how to build

## need apk-tools
Apko has a dependency on apk-tools. If you're not running on Alpine Linux or another apk-based distribution, the quickest way to get apko running is to use the OCI Container (Docker) image:
- docker pull cgr.dev/chainguard/apko:latest
## Create you image.yaml File
The image file that will replace the dockerfile will contain all the packages and configuration required to build your image.

## Run using apko image
```
docker run -v "$PWD":/work cgr.dev/chainguard/apko build images/alpine-base-rootless.yaml apko-alpine:edge apko-alpine.tar
docker run -v "$PWD":/work cgr.dev/chainguard/apko build images/wolfii.yaml apko-wolfii:test apko-wolfii.tar
```
## You can then load the generated tar image into a Docker environment
docker load < apko-alpine.tar

## You can also publish the image directly to a registry
apko publish examples/alpine-base.yaml myrepo/alpine-apko:test


# What about my application?
## Build the app as an APK package
Using melange we can build our app as an apk package. That later will be added as a package within the my image.