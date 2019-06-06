# phpMyAdmin on GAE

Cloud SQLのDBをphpMyAdminで管理できるようにします

## 環境

- PHP5.5  
- App Engine (1st generation)

## デプロイ方法

### phpMyAdminをダウンロード

https://www.phpmyadmin.net/downloads/ からダウンロードして解凍

### 設定ファイルを編集

設定ファイルをリネームする

`config.inc.sample.php` → `config.inc.php`

パスフレーズとCloud SQLへの接続設定を入力  
※Cloud SQLはTCPではなくUnix Socketで接続する

https://gitlab.com/freegufo/privete/mursts/phpmyadmin-on-gae/commit/f60d1452df719994402648f7787e08dfd22ddeac

### PHPの設定

php.iniを追加する

https://gitlab.com/freegufo/privete/mursts/phpmyadmin-on-gae/commit/c786aa6d6f945996c79c8e60d9763789ee455b7a

### App Engineの設定

app.yamlを追加

https://gitlab.com/freegufo/privete/mursts/phpmyadmin-on-gae/commit/12e378f126a4408451e9c9af3491338a02006890

### IAMの設定

必要に応じて設定する  

今回はApp Engineと別プロジェクトのCloud SQLに接続したので、App Engineのサービスアカウント([プロジェクト名]@appspot.gserviceaccount.com)に対して `roles/cloudsql.client` を付与した

### デプロイ

```sh
gcloud app deploy
```