# javasc-electron-env-test2
docker+javascript+electron env test
(開発中)

## 21/10/10 how to setup memo
1. VcXsrv をインストールして起動する。 https://rin-ka.net/windows-x-server/#toc3
2. ホスト側でipconfig してipアドレスを控える（イーサネット アダプター vEthernet (Default Switch):のところ
2. docker exec -it javascript_env_test2_app_1 bash でコンテナの中に入る。　（winptyコマンドを使えと怒られたら頭にwinpty つけて実行）
4. ホスト側のフォルダ　node_moduleフォルダを削除する
1. コンテナ側でyarnを実行
1. export DISPLAY=ipアドレス:0.0 先ほどのipアドレスを入力して実行する。
1. electronのチュートリアルをgithubから持ってきてapp直下にいれる。（一応既にいれてある）　 https://github.com/electron/electron-quick-start.git
1. yarn startでelectronが立ち上がってHello world が表示されたらOK
