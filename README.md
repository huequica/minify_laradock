# minify_laradock

命名ずいぶん強気だなこいつ

# なにこれ？
そこそこ小さい構成でとりあえずlaravelプロジェクト始める人向けの `docker-compose.yml` ファイルなどのテンプレート

# セットアップ

1. `git clone` してくる
2. `mkdir server` でディレクトリを作る(名前同じじゃないとつらいかも)
3. 素の状態で `docker-compose up`する。
4. プロジェクトを作る(新規作成でない場合は次に飛ばす)

```
# まずコンテナに入る
$ docker-compose exec php bash

# PHPコンテナにはcomposerを入れてあるのでそのまま叩く
$ composer create-project laravel/laravel=5.5 ./

# コンテナから抜ける
$ exit
```

5. `docker-compose.yml`のコメントアウトを一部外す

```docker-compose.yml
  # composerの依存をインストールするやつ。upしたときに立ち上がって終わると勝手に消える
  # 初回セットアップ以降は↓のコメントアウトを消してください
  # composer_depend_installer:
  #   container_name: composer_installer
  #   build:
  #     context: .
  #     dockerfile: ./docker/php/Dockerfile
  #   volumes:
  #     - ./server:/var/www
  #   command: composer install
```

この部分を有効化してやることで、 `composer.json` などが更新されていた場合 `docker-compose up` した時に自動インストールされる