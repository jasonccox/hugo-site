FROM jasonccox/git-personal-builder:latest-arm64
LABEL maintainer="me@jasoncarloscox.com"
EXPOSE 80

RUN apk add --no-cache hugo curl
COPY build /usr/bin/

CMD ["build"]
