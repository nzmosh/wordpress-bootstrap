# wordpress-bootstrap

[WP-CLI](http://wp-cli.org/)と[SQLite](http://www.dbonline.jp/sqlite/)を使用したWordPress環境のテンプレートです。  
WordPress環境がディレクトリ内で完結するので、チームで実装する場合に便利です。

## 使い方

### 1. デフォルトのまま使う場合

デフォルトだと`www`ディレクトリ（ドキュメントルート）が作成され、その中にWordPressがインストールされます。

```
$ mkdir yourSiteName
$ cd yourSiteName
$ curl -sL https://raw.githubusercontent.com/mgaoshima/wordpress-bootstrap/master/install.sh | sh
$ wp server --path www   # http://localhost:8080
```


### 2. 設定を変更して使う場合

```
$ git clone https://github.com/mgaoshima/wordpress-bootstrap
$ rm -rf .git
$ git init      # プロジェクトのgitリポジトリとして初期化
$ git add . -A  # すべてのファイルをGit管理下に置くのがよいと思う
```

`install.sh` の冒頭に設定があるので、適宜修正して下さい。

```
$ ./install.sh
$ wp server --path=www   # http://localhost:8080
```


## 備考

- デフォルトのWordPressアカウントは`admin`、パスワードも`admin`です。
- `wp-cli`がインストールされていない場合は自動でインストールされるので注意して下さい（suパスワード要求あり）
- データベースとして[SQLite Integration](http://dogwood.skr.jp/wordpress/sqlite-integration-ja/)経由でSQLiteを使用しているので、たまに動かないプラグインがあります。
- `www/wp-content/database/.ht.sqlite` がDBファイルです。そのままデプロイできると思いますが、ブラウザから直接アクセスされないようにする必要があります。
- `http://localhost:8080/wp-content/database/phpliteadmin.php` から[phpLiteAdmin](https://code.google.com/p/phpliteadmin/)に入れます。
- ホスト名は[Dynamic Hostname](https://wordpress.org/plugins/dynamic-hostname/)プラグインにより自動で書き換えられるので、任意で構いませんが、DBに登録される内容は`http://wordpress.local`です。
- Dynamic Hostnameプラグインは公式のものではなく、ポート番号付きのホスト名でも動くようにした[カスタマイズ版](https://github.com/mgaoshima/dynamic-hostname/tree/temp-use)を使用しています。


## Licence

MIT
