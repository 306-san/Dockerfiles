FROM python:3-slim-buster

WORKDIR /tmp

RUN pip install awscli
RUN set -ex \
    && export LANG=ja_jp.utf-8 \
    && apt update \
    && apt upgrade \
    && apt install -y --no-install-recommends jq curl unzip git pkg-config bash-completion kubectx openssh-client \
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
    && chmod +x ./kubectl \
    && mv ./kubectl /usr/local/bin/kubectl \
    # Install kube-prompt
    && curl -Ls "https://api.github.com/repos/c-bata/kube-prompt/releases/latest" -o repo_data.json \
    && DOWNLOAD_URL=$(cat repo_data.json | jq -r '.assets[] | select(.name | test("linux_amd64")) | .browser_download_url') \
    && DOWNLOAD_VERSION=$(cat repo_data.json | jq -r .tarball_url | grep -o '[^/v]*$') \
    && curl -Ls $DOWNLOAD_URL -o kube-prompt-$DOWNLOAD_VERSION.zip \
    && mkdir kube-prompt-$DOWNLOAD_VERSION \
    && unzip kube-prompt-$DOWNLOAD_VERSION.zip -d kube-prompt-$DOWNLOAD_VERSION  \
    && mv kube-prompt-$DOWNLOAD_VERSION/kube-prompt  /usr/local/bin/kube-prompt \
    # Install k9s
    && DOWNLOAD_VERSION="0.9.3" \
    && DOWNLOAD_URL="https://github.com/derailed/k9s/releases/download/$DOWNLOAD_VERSION/k9s_${DOWNLOAD_VERSION}_Linux_x86_64.tar.gz" \
    && curl -Ls $DOWNLOAD_URL -o k9s-$DOWNLOAD_VERSION.tar.gz \
    && mkdir k9s-$DOWNLOAD_VERSION \
    && tar -xvzf k9s-$DOWNLOAD_VERSION.tar.gz  --directory k9s-$DOWNLOAD_VERSION \
    && mv k9s-$DOWNLOAD_VERSION/k9s  /usr/local/bin/k9s \
    && echo "source /etc/profile.d/bash_completion.sh" >> ~/.bashrc \
    && apt -y clean \
    && apt auto-remove \
    && rm -rf /tmp/* \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /

CMD ["/bin/bash"]