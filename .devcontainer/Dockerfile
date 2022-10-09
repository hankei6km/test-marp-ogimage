FROM ghcr.io/hankei6km/h6-dev-containers:node


ARG USERNAME=vscode

USER root
# Install google-chrome
# https://github.com/puppeteer/puppeteer/blob/main/docs/troubleshooting.md#running-puppeteer-in-docker
# - add fonts-noto-cjk
RUN apt-get update \
    && apt-get install -y wget gnupg \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
    && apt-get update \
    && apt-get install -y google-chrome-stable fonts-ipafont-gothic fonts-wqy-zenhei fonts-thai-tlwg fonts-kacst fonts-freefont-ttf libxss1 \
    && apt-get install -y fonts-noto-cjk \
      --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

WORKDIR "/home/${USERNAME}"
USER ${USERNAME}