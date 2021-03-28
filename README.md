## php_framework_from_scratch

パーフェクトPHPを参考にフレームワークをゼロから作る試み。フレームワークに振り回されたくない！

## 理解のための雑記
index.phpがエントリポイントで、requireすることでbootstrap.phpを実行およびAppicationを初期化している。
リクエストが届いたらまずはurlを解析して、該当するコントローラーとアクションを決定(run)
特定次第、コントローラーをディレクトリ内から探して、runを実行する(runAction)
各処理の終了後に、responseを返す(response->send())