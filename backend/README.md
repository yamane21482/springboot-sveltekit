# SpringBoot と、Postgresql を使用したアプリケーション

## プロジェクト構成

プロジェクトの構成は以下の通りです。

```bash
.
├── Dockerfile
├── db
│   └── password.txt
├── docker-compose.yml
├── pom.xml
├── src
├── target
└── README.md
```

## 起動方法

### 1. コンテナのビルド

```bash
$ docker compose build
```

### 2. コンテナの起動

```bash
$ docker compose up -d
```

-d: バックグラウンドで起動

※ コンテナのビルドと起動は以下のコマンドで同時に行うこともできます。

```bash
$ docker compose up -d --build
```

### 3. コンテナが起動していることを確認

```bash
$ docker compose ps
```

以下のように表示されれば OK です。

```bash
NAME                IMAGE               COMMAND                  SERVICE             CREATED             STATUS              PORTS
backend-backend-1   backend-backend     "java -cp app:app/li…"   backend             2 seconds ago       Up 1 second         0.0.0.0:8000->8080/tcp, :::8000->8080/tcp
backend-db-1        postgres            "docker-entrypoint.s…"   db                  3 seconds ago       Up 1 second         0.0.0.0:5432->5432/tcp, :::5432->5432/tcp
```

アプリケーションが起動したら、以下の URL にアクセスしてみてください。

```bash
http://localhost:8000
```

※ バックエンドのコンテナのポート番号を 8000 に設定するのは、ローカルでの起動時にポート番号の衝突を避けるためです。

ブラウザに以下のような画面が表示されれば OK です。
![](./images/localhost_8000.png)

### コンテナの停止

```bash
$ docker compose down
```

以下のように表示されれば OK です。

```bash
[+] Running 3/3
 ✔ Container backend-backend-1      Removed
 ✔ Container backend-db-1           Removed
 ✔ Network backend_spring-postgres  Removed
```
