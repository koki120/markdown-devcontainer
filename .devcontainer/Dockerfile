# Alpine Linuxからベースイメージを取得
FROM alpine:latest

ARG USER_ID="10000"
ARG GROUP_ID="10000"
ARG USER_NAME="vscode"

RUN addgroup -S -g "${GROUP_ID}" "${USER_NAME}" && \
  adduser -u "${USER_ID}" -G "${USER_NAME}" -D "${USER_NAME}"

RUN sudo chown -R vscode /workspaces/markdown-dev

USER "${USER_ID}"
