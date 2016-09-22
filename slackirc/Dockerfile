FROM alpine:edge

RUN echo "@testing http://dl-cdn.alpinelinux.org/alpine/edge/testing" \
      >> /etc/apk/repositories \
    && apk --no-cache add nodejs python build-base entrykit@testing \
    && npm install -g slack-irc \
    && apk --no-cache del build-base python

RUN apk --no-cache add curl \
    && curl -sSL https://github.com/gliderlabs/sigil/releases/download/v0.4.0/sigil_0.4.0_Linux_x86_64.tgz \
      | tar -zxC /usr/local/bin \
    && apk --no-cache del curl

ENV NODE_ENV development
ENV SLACK_LOG_LEVEL debug
ENV CONFIG_FILE=/etc/slackirc.json

COPY ./config.json.tmpl /etc/slackirc.json.tmpl

ENTRYPOINT ["render", "/etc/slackirc.json", "--", "slack-irc"]
