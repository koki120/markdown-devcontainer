FROM alpine:latest

ARG USER_ID=10000
ARG GROUP_ID=10000
ARG USER_NAME=vscode

RUN apt-get update && apt-get install -y \
  chromium-browser \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN addgroup -S -g "${GROUP_ID}" "${USER_NAME}" && \
  adduser -u "${USER_ID}" -G "${USER_NAME}" -D "${USER_NAME}" && \
  mkdir -p /workspaces/markdown-dev/documents && \
  chown -R "${USER_ID}:${GROUP_ID}" /workspaces/markdown-dev/documents 

USER "${USER_NAME}"