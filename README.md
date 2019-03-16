------------------------------------------------------
curl dev docker container
------------------------------------------------------

[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jamesfuller/libcurl-dev-dependencies-linux.svg)](https://cloud.docker.com/repository/docker/jamesfuller/libcurl-dev-dependencies-linux)


Docker image containing dependencies required for [libcurl](https://curl.haxx.se) development.

The docker image is hosted at [docker hub](https://hub.docker.com) here:

[jamesfuller/libcurl-dev-dependencies-linux](https://cloud.docker.com/repository/docker/jamesfuller/libcurl-dev-dependencies-linux)


The following dockerfile illustrates how to create an image with your own fork of [https://github.com/curl/curl](https://github.com/curl/curl)

```
FROM jamesfuller/libcurl-dev-dependencies-linux

ENV CURL_SOURCE_DIR=/src/curl
ENV CURL_GIT_REPO=https://github.com/<your github >/curl.git

RUN mkdir -p ${CURL_SOURCE_DIR}
RUN chmod -R 777 ${CURL_SOURCE_DIR}
RUN chown -R root:root ${CURL_SOURCE_DIR}

RUN git clone ${CURL_GIT_REPO} ${CURL_SOURCE_DIR}

RUN cd /src/curl && ./buildconf

CMD ["/bin/bash"]
```


**Note**: nix images are experimental (and likely to not work)
