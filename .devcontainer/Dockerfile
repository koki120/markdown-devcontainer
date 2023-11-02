FROM alpine:latest

ARG USER_ID=10000
ARG GROUP_ID=10000
ARG USER_NAME=vscode

RUN apk update && apk add --no-cache \
    chromium \
    && rm -rf /var/cache/apk/*

RUN addgroup -S -g "${GROUP_ID}" "${USER_NAME}" && \
  adduser -u "${USER_ID}" -G "${USER_NAME}" -D "${USER_NAME}" && \
  mkdir -p /workspaces/markdown-dev/documents && \
  chown -R "${USER_ID}:${GROUP_ID}" /workspaces/markdown-dev/documents 

USER "${USER_NAME}"
