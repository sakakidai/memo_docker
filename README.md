# memo_dockerのコンテナ立ち上げ
### docker-syncのインストール

```
$ gem install docker-sync
$ brew install fswatch
$ brew install unison
$ brew install eugenmayer/dockersync/unox
```

### clone

```
$ git clone git@github.com:sakakidai/memo_docker.git
$ cd memo_docker
```

### envファイル作成

```
$ vi .env
LOCAL_FILE_PATH=<memoのローカルのファイルパスを記述>
```

### docker-syncの起動

```
$ docker-sync start
```

### dockerの起動

```
docker-compose up -d
```

### コンテナに接続

```
$ docker-compose exec app bash
```

# コンテナ作成後
### 起動手順
1. docker-sync起動
2. docker起動

### dockerコマンド
```
# docker-syncのログを確認する
$ tail -f memo_docker/.docker-sync/daemon.log

# Dockerfileを訂正したとき
$ docker-compose up --build

# 停止
$ docker-compose stop

# 停止、コンテナ削除
$ docker-compose down

# コンテナ確認
$ dokcer ps -a

# イメージ確認
$ docker images

# ボリューム確認
$ docker volume ls
```
