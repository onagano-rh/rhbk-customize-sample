# Example of Authenticator SPI and Custom Theme

## ビルドとデプロイ

`KC_HOME`に(Red Hat build of) Keycloakがインストールされていること。

```shell
# Authenticator SPI のビルドとデプロイ
$ cd authenticator
$ cp target/authenticator-required-action-example.jar $KC_HOME/providers

# カスタムテーマのビルドとデプロイ
$ cd ../theme
$ cp target/keycloak-example-themes.jar $KC_HOME/providers

# サーバの起動
cd $KC_HOME
bin/kc.sh build
bin/kc.sh start --proxy=edge --hostname-strict=false
```

## 設定

テスト用のレルムを作成しそこに設定を行う。

基本的に Authenticator SPI の元である秘密の質問の例の [README.md](https://github.com/keycloak/keycloak/tree/release/22.0/examples/providers/authenticator) と同じである。

1. 認証フローでデフォルトのブラウザをコピーし、"Secret Question"をREQUIREDで追加。
2. Required Actionsで"Secret Question"を設定し秘密の質問の設定を強制。
3. ログインテーマを（このカスタマイズ用のHTMLテンプレートを含む）"secret-question"に設定。

テスト用のユーザを作成し、アカウント管理コンソール (http://localhost:8080/realms/test-realm/account/) にログインしてみて動作を確認する。

