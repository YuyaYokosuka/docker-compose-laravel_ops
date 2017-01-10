検証用なのでちゃんと仕えないかもしれないです

## ディレクトリ説明
```
.
├── Dockerfiles #Dockerfileを使って設定する場合、このフォルダ以下にパッケージ名でフォルダ作ってその中にDockerFileを収める。また、パッケージ内でインポートする必要がある場合はそのファイルもフォルダ内に含める
│   ├── nginx
│   │   ├── Dockerfile
│   │   └── server.conf #Laravelをapplication/に展開した時用のコンフィグ
│   └── php-fpm
│       └── Dockerfile
├── application #Laravelのリポジトリはこの下に展開する
├── docker-compose.yml #docker-composeの設定
└── readme.md #このファイルです
```

## 導入
- 初回のみ`docker-compose.yml`の`APP_KEY` を適切に設定し直して下さい
- docker,docker-composeをインストールする（ここはググって下さい）
当方バージョン情報
```
$ docker -v
Docker version 1.12.5, build 7392c3b
$ docker-compose -v
docker-compose version 1.9.0, build 2585387
```

- application以下にLaravelの実体を配置して下さい
	- このリポジトリではLaravelの公式をsubmodule化してるので、 `git submodule init` とかすればとりあえず動作確認できると思います
- あとは `docker-compose up --build` すれば立ち上がります。
	- 初回のみAppコンテナで `composer install` を行って下さい

## Tips
- よく使いそうなdocker-composeのコマンド

```
//デーモン化
$ docker-compose up --build -d

//各プロセスの現状確認
$ docker-compose ps
```

- Laravelのcomposer叩いたりマイグレーションしたりなんだりしたい

```
$ docker-compose exec app composer install
$ docker-compose exec app php artisan migrate
```
