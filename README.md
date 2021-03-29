## php_framework_from_scratch

パーフェクトPHPを参考にフレームワークをゼロから作る試み。フレームワークに振り回されたくない！

## 理解のための雑記
- index.phpがエントリポイントで、requireすることでbootstrap.phpを実行およびAppicationを初期化している。ClassLoaderで必要なファイル(coreとmodel配下)をrequireしてクラスを読み込み、Applicationで必要なクラスをinitializeしている。
- リクエストが届いたらまずはurlを解析して、該当するコントローラーとアクションを取得(run)
- 特定次第、コントローラーをディレクトリ内から探して(runAction)、runを実行する(Controller->run)。responseの返り値にcontentを設定する。
- 各処理の終了後に、responseを返す(response->send), Viewクラスがかえる場合はファイルを返す。