VAddyでVerificationファイルが設置できない環境で、検査対象サーバの手前にリバースプロキシサーバを設置して対応する方法です。

このディレクトリの、`nginx.conf`と`site.d/site.conf`が設定ファイルになります。  
`site.conf`に記載している`/var/www/html`がwebrootですので必要に応じて変えてください。
このwebrootに`vaddy-xxxxx.html`というようなVerificationファイルを設置してください。
このファイルがある時は、nginxがhtmlを返します。 それ以外のURLは裏のバックエンドサーバ（検査対象サーバ）に接続してコンテンツを返します。

## グローバル版
VAddy -> nginx(reverse proxy) -> OriginServer

## プライベート版
VAddy -> go-vaddyクライアント -> nginx(reverse proxy) -> OriginServer

プライベートネット版は、go-vaddyクライアントの設定ファイル  
https://github.com/vaddy/go-vaddy/blob/master/privatenet/conf/vaddy.conf.example  
の`VADDY_YOUR_LOCAL_IP`と`VADDY_YOUR_LOCAL_PORT`にnginxのIPとポート番号を指定してください。
