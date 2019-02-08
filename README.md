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


## 初期設定

Rails作成：
$ docker-compose run web rails new . --force --database=mysql

ビルド：
$ docker-compose build

DBファイル：
./config/database.yml

```ruby
default: &default
  adapter: mysql2
  encoding: utf8
  pool: 5
  username: root
  password: xxxxxxxx
  host: db
```

DB作成：
$ docker-compose run web bundle exec rake db:create

---

# Rails Base Create

## 1/3 Routing

./config/routes.rb

Add
`root 'boards#index'`

## 2/3 コントローラー作成

Create
小文字でコントローラー名 + `_controller.rb`

$ vim app/contoroller/boards_controller.rb

```ruby
class BoardsController < ApplicationController
  def index
  end
end
```

※コントローラー名 = キャメルケース
基本は ApplicationController を継承
index = （BoardsControllerの）indexアクション

## 3/3 アクション名のViewファイル作成

```
$ mkdir app/views/boards 
$ vim app/views/boards/index.html.erb

<h1>Hello World</h1>
```

---

# 他環境時（違うPC）

[docker-compose で Rails の開発環境を作る - Qiita](https://qiita.com/skyriser/items/2cf98b747ed6577cc5ee)

$ docker-compose run web rake db:create
$ docker-compose run web rake db:migrate

config/initializers/new_framework_defaults.rb
↑ 全 #閉じ
[Obsoleted method `halt_callback_chains_on_return_false` still called in Rails 5.2 · Issue #32653 · rails/rails · GitHub](https://github.com/rails/rails/issues/32653)
5.2系にした時に出る？

config/environments/production.rb
# config.i18n.fallbacks = true
config.i18n.fallbacks = [I18n.default_locale]
