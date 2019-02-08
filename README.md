# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## 基本操作

起動 再起動

ログ無し（通常こちらを使用）
$ docker-compose up -d

ログが流れる版
$ docker-compose up

停止
$ docker-compose stop

起動失敗時
$ rm tmp/pids/server.pid
$ docker-compose up

コンテナ削除 (再起可)
$ docker-compose down

起動状態確認
$ docker ps

起動していないものも含めて確認
$ docker ps -a
 
 ブラウザ
[Ruby on Rails](http://localhost:3000/)

### 削除
[Dockerイメージとコンテナの削除方法 - Qiita](https://qiita.com/tifa2chan/items/e9aa408244687a63a0ae)


