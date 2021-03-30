## php_framework_from_scratch

パーフェクトPHPを参考にフレームワークをゼロから作る試み。フレームワークに振り回されたくない！

## 理解のための雑記
- index.phpがエントリポイントで、requireすることでbootstrap.phpを実行およびAppicationを初期化している。ClassLoaderで必要なファイル(coreとmodels配下)をrequireしてクラスを読み込み、Applicationで必要なクラスをinitializeしている(Application->initialize)。
- リクエストが届いたらまずはurlを解析して、該当するコントローラーとアクションを取得(run)
- 特定次第、コントローラーをディレクトリ内から探してアクションを特定し(runAction)、runを実行する(Controller->run)。responseの返り値にcontentを設定する。
- 各処理の終了後に、responseを返す(response->send), Viewクラスがかえる場合はファイルを返す。

laravelについて
- サービスコンテナ => オブジェクトをインスタンス化する機能、依存解決と、インスタンス初期化時の条件を加えることができる
- サービスプロバイダ、以下の通り、config/app.phpに登録されている、サービスコンテナに登録する一覧。registerメソッドでインスタンス化方法を記述。bindingとsingletonでインスタンス化の設定を選ぶことができる。
> Laravelに含まれているconfig/app.phpファイルを開けば、providers配列が見つかるでしょう。そこにある全サービスプロバイダクラスが、アプリケーションのためにロードされます。ほとんどのプロバイダは、すべてのリクエストで必ずロードされるとは限らず、そのプロバイダが提供するサービスが、実際に必要なときにのみロードされる「遅延」プロバイダです。

参考
https://readouble.com/laravel/8.x/ja/container.html
https://readouble.com/laravel/8.x/ja/providers.html
https://qiita.com/minato-naka/items/f05b023950ce544a8bec