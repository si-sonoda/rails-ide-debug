# Railsでリモートデバッグをやってみる

## 必要なもの
* Docker for mac
* git

## 手順
1. このプロジェクトをcloneする
    `https://github.com/si-sonoda/rails-ide-debug.git ~/rails-ide-debug`
2. ターミナルでプロジェクトまでcdする
    `cd ~/rails-ide-debug`
3. コンテナのビルド
   `docker-compose build`
4. コンテナの立ち上げ
   `docker-compose up`
5. http://localhost:3000 へアクセス、画面が表示されるとOK
