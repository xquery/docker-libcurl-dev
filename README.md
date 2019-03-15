------------------------------------------------------
curl dev nix docker container
------------------------------------------------------

Docker image containing all deps required for libcurl development.

The docker image

 [jamesfuller/libcurl-dev-dependencies-nix](https://cloud.docker.com/repository/docker/jamesfuller/libcurl-dev-dependencies-nix)

contains all the dependencies required to build and test libcurl.

To generate an image with your own fork of https://github.com/curl/curl


```
FROM jamesfuller/libcurl-dev-dependencies-nix

ENV CURL_SOURCE_DIR=/src/curl
ENV CURL_GIT_REPO=https://github.com/<your github >/curl.git

RUN mkdir -p ${CURL_SOURCE_DIR}
RUN chmod -R 777 ${CURL_SOURCE_DIR}
RUN chown -R root:root ${CURL_SOURCE_DIR}

RUN git clone ${CURL_GIT_REPO} ${CURL_SOURCE_DIR}

RUN cd /src/curl && ./buildconf

CMD ["/bin/bash"]
```
