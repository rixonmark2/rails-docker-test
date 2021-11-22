# 環境構築手順
1. プロジェクトを置きたいディレクトリに移動
```
cd hoge
```

2. リポジトリをクローン
```
git clone https://github.com/rixonmark2/rails-docker-test.git
```

3. クローンしたプロジェクトに移動
```
cd rails-docker-test
```

4. Dockerコンテナ起動
```
docker-compose up -d --build
```

5. DB作成
```
docker-compose exec app rails db:create
```

6. [ローカルホスト](http://localhost:8002/)にアクセスし確認