FROM nginx:1.27-alpine

ARG BUILD_COMMIT=dev
ARG BUILD_TIME=

COPY . /usr/share/nginx/html

RUN echo "window.BUILD_INFO = { commit: \"${BUILD_COMMIT}\", time: \"${BUILD_TIME}\" };" > /usr/share/nginx/html/build-info.js
