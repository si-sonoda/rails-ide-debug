FROM ruby:2.6.0

RUN apt-get update -qq && \
    apt-get install -y build-essential \
                       libpq-dev\
                       vim \
                       curl

# https://qiita.com/jungissei/items/c58bd1158cd909540b26
RUN mkdir /api

ENV APP_ROOT /api
WORKDIR $APP_ROOT

ADD ./api/Gemfile $APP_ROOT/Gemfile
ADD ./api/Gemfile.lock $APP_ROOT/Gemfile.lock

# Node.jsとyarnのインストール
# バージョンは自分のローカルのバージョンに合わせた
# https://thr3a.hatenablog.com/entry/20190221/1550748615
ENV NODE_VERSION 14.14.0

# install nodejs
RUN curl --compressed "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.xz" > /tmp/node.tar.xz && \
  tar -xJf /tmp/node.tar.xz -C /usr/local --strip-components=1 && \
  ln -s /usr/local/bin/node /usr/local/bin/nodejs && \
  rm /tmp/node.tar.xz


ENV YARN_VERSION 1.22.10

# install yarn
RUN curl -L --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz" > /tmp/yarn.tar.gz && \
  tar -xzf /tmp/yarn.tar.gz -C /opt && \
  ln -s /opt/yarn-v$YARN_VERSION/bin/yarn /usr/local/bin/yarn && \
  ln -s /opt/yarn-v$YARN_VERSION/bin/yarnpkg /usr/local/bin/yarnpkg && \
  rm /tmp/yarn.tar.gz

RUN bundle install --jobs=8

COPY ./api /api

RUN yarn install