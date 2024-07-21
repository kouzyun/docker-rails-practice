# DockerでオリジナルのRails開発環境を構築する
DockerでLaravel環境を構築し、dev-rails.menta.work(rails)を立ち上げて監視する。

## 表示確認
サイトが表示されることを確認。
![rails表示証跡](https://github.com/kouzyun/MENTA/assets/63705498/37eff4be-676f-4a7f-b699-1940e987850f)


## 構築手順
1. `hostsファイル`に以下の設定を行う。

```
hosts
127.0.0.1 dev-rails.menta.work
```

2. /rails/docker/devフォルダまでターミナルで移動し、`docker-compose build`とコマンド投入しコンテナをビルド。

3. `docker-compose up -d`とコマンド投入し、コンテナを立ち上げる。

4. `docker exec -it rails-app bash`とコマンド投入し`appコンテナ`へ接続。

5. `rails db:migrate`とコマンド投入し、マイグレーション実施。

## DB、redisへの接続確認

`appコンテナ`にてdbとredisへの接続確認を実施。

・DB<br>
`mysql -u root -h db -p`とコマンド投入し接続確認。<br>
<img width="600" alt="mojikyo45_640-2.gif" src="https://github.com/kouzyun/MENTA/assets/63705498/94eb34f5-f484-46ed-b641-1220d861c3fa">

・redis<br>
`redis-cli -h redis`とコマンド投入し接続確認。<br>
<img width="600" alt="mojikyo45_640-2.gif" src="https://github.com/kouzyun/MENTA/assets/63705498/a3c27e5a-4670-4409-ad0a-841a2d4f85e5">