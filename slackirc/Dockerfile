FROM alpine:edge

RUN apk --no-cache add nodejs-current yarn \
  && mkdir /app

COPY package.json /app
COPY yarn.lock /app
WORKDIR /app

RUN yarn

ENTRYPOINT ["/app/node_modules/.bin/slack-irc"]
