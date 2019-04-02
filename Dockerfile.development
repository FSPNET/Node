FROM node:10.15-alpine

ARG NODE_ENV=development
ENV NODE_ENV=${NODE_ENV}

WORKDIR /usr/src/app

RUN apk update &&\
    apk add --no-cache curl gcc g++ wget zsh yarn && \
    apk add --no-cache python3 && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi && \
    rm -rf /root/.cache && rm -rf /var/cache/apk/*
    
RUN apk add --no-cache --virtual .build-deps git && \
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" && \
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git /root/.oh-my-zsh/plugins/zsh-syntax-highlighting && \
    git clone https://github.com/zsh-users/zsh-autosuggestions /root/.oh-my-zsh/plugins/zsh-autosuggestions && \
    apk del .build-deps
COPY .zshrc /root/.zshrc

RUN true &&\
    npm config set registry https://registry.npm.taobao.org && \
    npm config set disturl https://npm.taobao.org/dist && \
    npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass && \
    npm config set electron_mirror https://npm.taobao.org/mirrors/electron && \
    npm config set puppeteer_download_host https://npm.taobao.org/mirrors && \
    npm config set chromedriver_cdnurl https://npm.taobao.org/mirrors/chromedriver && \
    npm config set operadriver_cdnurl https://npm.taobao.org/mirrors/operadriver && \
    npm config set phantomjs_cdnurl https://npm.taobao.org/mirrors/phantomjs && \
    npm config set selenium_cdnurl https://npm.taobao.org/mirrors/selenium && \
    npm install -g npm && \
    # fix yarn permission denied  https://github.com/nodejs/docker-node/issues/661
    chmod a+x /usr/local/bin/yarn && \
    # yarn china mirrors  https://github.com/nodejs/docker-node/issues/386
    yarn config set registry https://registry.npm.taobao.org || true

VOLUME [ "/usr/src/app" ]

EXPOSE 3000

CMD [ "zsh" ]