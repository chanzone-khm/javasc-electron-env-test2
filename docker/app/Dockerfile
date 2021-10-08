# 参考https://zukucode.com/2019/07/docker-electron-dev.html
FROM ubuntu

# update
RUN apt-get -y update && apt-get -y upgrade

# install basic packages

RUN apt-get install -y \
sudo \
bzip2 \
vim

# libgtkextra-dev のところでlocationを入力する謎の項目があるが、入力してもフリーズする。tzdataをやると解消する
# Dpkg ~~ をインストールするとkeyエラーみたいなやつが解消する
RUN apt-get install -y tzdata \
    && apt-get install -y  -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" keyboard-configuration \
    && apt-get -y install libgtkextra-dev libgconf2-dev libnss3 libasound2 libxtst-dev libxss1 libgtk-3-0

RUN apt-get -y update \
    && apt-get install -y language-pack-ja-base language-pack-ja fonts-noto-cjk fcitx-mozc \
    && im-config -n fcitx

# windows用にビルドするために必要
RUN dpkg --add-architecture i386 \
    && apt-get update \
    && apt-get install -y wine-stable wine32

# nodejsとyarnをインストールするために必要
RUN apt-get update \
  && apt-get install -y curl


# nodejsのインストールで時間不一致エラーが出るので対応策 うまくいかず hwclock --hctosysのどっちかでかいけつできそう
# RUN sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"
# RUN sudo apt update

# nodejsのインストールで時間不一致エラーが出るので対応策
# RUN sudo hwclock --hctosys
# nodejsのインストール
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash - \
    && apt-get install -y nodejs



# yarnをインストール
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/+sources.list.d/yarn.list \
    && apt-get update && apt-get install yarn

ENV GTK_IM_MODULE=xim \
    QT_IM_MODULE=fcitx \
    XMODIFIERS=@im=fcitx \
    DefalutIMModule=fcitx

RUN locale-gen ja_JP.UTF-8  
ENV LANG=ja_JP.UTF-8 \
    LC_ALL=ja_JP.UTF-8

# add user
ARG DOCKER_UID=1000
ARG DOCKER_USER=docker
ARG DOCKER_PASSWORD=docker
RUN useradd -m \
  --uid ${DOCKER_UID} --groups sudo ${DOCKER_USER} \
  && echo ${DOCKER_USER}:${DOCKER_PASSWORD} | chpasswd

USER ${DOCKER_USER}

WORKDIR /home/${DOCKER_USER}/app