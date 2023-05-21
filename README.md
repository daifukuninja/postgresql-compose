# README

## postgresql 環境を Docker Compose で構築する

### `env`の準備

直下のディレクトリで以下を実行

`cp .env.sample .env`

環境変数`POSTGRES_PASSWORD`を任意に設定する

### 初回実行時の準備

Docker network を作成する

`docker network create postgres-dev`

### Dockerの操作

#### コンテナの起動

`docker compose up -d`

#### コンテナの終了

`docker compose down`

データベースのデータはDockerボリュームに保存しているので、コンテナを終了しても消えません。
起動コマンドで再度コンテナを開始すると、同じデータが残った状態になります。

#### データ(ボリューム)の削除

`docker volume rm postgres-data`

#### コンテナにログイン

`docker compose exec db /bin/sh`

#### コンテナにログイン

`docker compose exec db /bin/sh`

#### コンテナからログアウト

`exit`

### DBの操作(コンテナにログイン後)

#### postgresql に接続する

`psql -h localhost -p 5432 -U postgres`

#### データベースの作成

`create database pydb;`

`pydb`の部分は任意に変更できます。

#### データベースの一覧を表示

`\l`

#### データベースに接続する

`\c pydb`

`pydb`の部分は作成したデータベース名を指定します。

### sqlファイルの実行

`\i /home/sql/create_users.sql`

`sql`ディレクトリに作成したファイルは、コンテナ内の`/home/sql`ディレクトリにマウントされています。

### postgresqlから切断する

`quit`
