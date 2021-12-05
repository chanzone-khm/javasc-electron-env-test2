# 自分の開発用メモ

GUI app development using docker × electron × nodejs

## Release note

| date     | note                                                                                                                                |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 21/12/05 | add <br> <p> <ul> <li>bootstrap5.1.3</li> <li>poppers.js</li> <li> jquery</li> </ul> bootstrap icons</p> <br> add devtools prettier/ eslint / eslint-config-prettier |

## 21/12/05 how to setup

### 初回起動

1. clone する
2. ホスト側 ターミナルで id と売って、UID を控える。
3. clone 先のフォルダに移動し、docker/app/dockerfile を開いて、UID の数値を上記取得した値に書き換える。
4. docker-compose.yml ファイルがあるフォルダに移動し docker-compose up -d
5. VcXsrv をインストールして起動する。 https://rin-ka.net/windows-x-server/#toc3
6. docker exec -it javascript_env_test2_app_1 bash でコンテナの中に入る。
7. コンテナ側で yarn を実行(package.json に記載されたアプリがインストールされる)
8. yarn start で electron が立ち上がって Hello world が表示されたら OK

### 初回起動以降

1. docker-compose up -d で起動
2. visual studio code 等でコンテナにアクセスし開発

### ライブラリを追加する場合

1. yarn add / npm 等でパッケージを追加
