How to prepare a new docker image 
=================================

Prepare your docker environment
-------------------------------

1. Install QEMU driver to allow docker run executables for foreing architectures
     docker run --privileged --rm tonistiigi/binfmt --install all
2. Create a  new builder: docker buildx create --name mybuilder
3. Check new build supports at least linux/arm64 and linux/amd64

Prepare a new image
-------------------


1. Make modifications as needed to the Dockerfile
2. Build the docker image for amd64 and arm64 platforms (further information regarding multiplatform can be found here: https://docs.docker.com/build/building/multi-platform/#build-multi-platform-images)

    cd scripts
    docker build -t ghcr.io/tiacsys/bridle-dojo:YOUR_TAG \
               --platform linux/amd64,linux/arm64 \
               --builder mybuilder \
               --push .


    