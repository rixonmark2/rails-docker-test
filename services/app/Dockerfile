FROM ruby:3.0.2

# リポジトリを更新し依存モジュールをインストール
RUN apt-get update -qq && \
    apt-get install -y build-essential nodejs=12.22.5~dfsg-2~11u1

# yarnパッケージ管理ツールインストール
RUN apt-get update && apt-get install -y curl apt-transport-https wget && \
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
    apt-get update && apt-get install -y yarn

# ルート直下にtest-appという名前で作業ディレクトリを作成（コンテナ内のアプリケーションディレクトリ）
WORKDIR /test-app

# ホストのGemfileとGemfile.lockをコンテナにコピー
ADD ./test-app/Gemfile /test-app/Gemfile
ADD ./test-app/Gemfile.lock /test-app/Gemfile.lock

# bundle installの実行
RUN bundle install

# puma.sockを配置するディレクトリを作成
RUN mkdir -p tmp/sockets && \
    mkdir -p tmp/pids

CMD bundle exec puma -C config/puma.rb