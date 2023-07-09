# todo_api

## 技術スタック
- Rails：6.1.4.1
- React：18.2.0
- ChakraUI：2.7.1

## 機能概要

本プロジェクトは、一覧表示、作成、削除、完了機能を持つシンプルなTODOアプリケーションです。以下に各機能のGIFを用いた詳細を説明します。

### タスク一覧機能
全てのタスクを一覧表示します。作成されたタスクは、完了しているかどうかに関係なく、一覧で表示されます。

![タスク一覧機能](https://i.gyazo.com/53fb392f3368fab36f41649ca0f45deb.gif)

### タスク作成機能
新たなタスクを作成します。タスク名を入力し、「タスクを作成」ボタンを押すと、新たなタスクが一覧に追加されます。

![タスク作成機能](https://i.gyazo.com/6c84e4a58777bca9919204169255b312.gif)

### タスク削除機能
既存のタスクを削除します。一覧からタスクの右側に表示される削除アイコン（×）をクリックすると、該当のタスクが一覧から削除されます。

![タスク削除機能](https://i.gyazo.com/f3b4e7b63cfab64dd90585f1c9256968.gif)

### タスク完了機能
既存のタスクを完了状態に変更します。一覧から該当のタスクをチェックすると、そのタスクは完了状態となります。

![タスク完了機能](https://i.gyazo.com/cb0c88a4c52c3d52dc2047b24f2ef693.gif)

これらの機能を組み合わせて、ユーザーは自身のタスクを効率よく管理することができます。

## Docker コンテナへの接続方法

このプロジェクトでは、Dockerを使用して複数のサービス（api、db、front）を容易に管理しています。以下の手順で各サービスのDockerコンテナに接続できます。

まず、ターミナルで以下のコマンドを実行します。これにより稼働中のコンテナの一覧が表示されます。

```bash
docker compose ps
```

表示されるコンテナの一覧は以下の通りです：

```
NAME                COMMAND                  SERVICE             STATUS              PORTS
todo_api-api-1      "entrypoint.sh /bin/…"   api                 running             0.0.0.0:3001->3000/tcp
todo_api-db-1       "docker-entrypoint.s…"   db                  running             0.0.0.0:3306->3306/tcp, 33060/tcp
todo_api-front-1    "docker-entrypoint.s…"   front               running             0.0.0.0:3000->3000/tcp
```

この一覧から、接続したいサービス（例えば`api`）を選び、次のコマンドでそのコンテナに接続します：

```bash
docker-compose exec api bash
```

これで`api`サービスのコンテナ内に接続できます。このコマンドはコンテナ内でbashシェルを開始します。

同様に、他のサービス（`db`、`front`）に接続するには、それぞれ以下のコマンドを実行します：

```bash
docker-compose exec db bash
docker-compose exec front bash
```

これらのコマンドを使用して各コンテナに接続し、必要な操作を行うことができます。
