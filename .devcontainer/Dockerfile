# https://github.com/devcontainers/images/tree/main/src/typescript-node
FROM mcr.microsoft.com/devcontainers/typescript-node


ARG USERNAME=node

USER root
# Install google-chrome
# https://github.com/puppeteer/puppeteer/blob/main/docs/troubleshooting.md#running-puppeteer-in-docker
# - add fonts-noto-cjk
RUN apt-get update \
  && apt-get install -y wget gnupg \
  && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
  && sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
  && apt-get update \
  && apt-get install -y google-chrome-stable libxss1 \
  --no-install-recommends \
  && apt-get install -y fonts-noto-cjk fonts-noto-cjk-extra\
  --no-install-recommends \
  && rm -rf /var/lib/apt/lists/*
COPY first-run-notice.txt /usr/local/etc/vscode-dev-containers/first-run-notice.txt

WORKDIR "/home/${USERNAME}"
USER ${USERNAME}

# Use Noto fonts as default fonts force
COPY --chown="${USERNAME}" fonts.conf "/home/${USERNAME}/.config/fontconfig/fonts.conf"
RUN fc-cache -r