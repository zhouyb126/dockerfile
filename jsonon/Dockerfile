FROM nginx:1.13.12-alpine

LABEL maintainer="mritd <mritd1234@gmail.com>"

ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}
ENV JSONON_GIT_ADDR https://github.com/awesomes-cn/jsonon.git

RUN apk upgrade --update \
    && apk add bash tzdata git \
    && rm -rf /usr/share/nginx/html \
    && git clone ${JSONON_GIT_ADDR} /usr/share/nginx/html \
    && rm -rf /usr/share/nginx/html/.git \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /var/cache/apk/*

CMD ["nginx","-g","daemon off;"]
