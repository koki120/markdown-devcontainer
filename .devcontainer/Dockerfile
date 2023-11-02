FROM alpine:latest

ARG USER_ID=10000
ARG GROUP_ID=10000
ARG USER_NAME=vscode

RUN apk update && apk add --no-cache \
  chromium \
  ask-japanese \
  fonts-ipafont \
  fonts-ipaexfont \
  curl \
  unzip \
  fontconfig \
  && rm -rf /var/cache/apk/*

# Download Noto Sans font
RUN curl -o /tmp/NotoSansCJKjp-hinted.zip https://noto-website-2.storage.googleapis.com/pkgs/NotoSansCJKjp-hinted.zip \
  && unzip -o -d /usr/share/fonts/noto /tmp/NotoSansCJKjp-hinted.zip \
  && chmod 644 /usr/share/fonts/noto/*.otf \
  && fc-cache -fv

RUN addgroup -S -g "${GROUP_ID}" "${USER_NAME}" && \
  adduser -u "${USER_ID}" -G "${USER_NAME}" -D "${USER_NAME}" && \
  mkdir -p /workspaces/markdown-dev/documents && \
  chown -R "${USER_ID}:${GROUP_ID}" /workspaces/markdown-dev/documents 

USER "${USER_NAME}"
