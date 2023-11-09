# Serverspecのインストールからテストコードの実行まで
1. Gemfileに`gem 'serverspec'`を追加する。
2. `bundle`を実行する。
3. `spec_helper.rb`ファイルの先頭に以下のコードを追加する。

```ruby
require 'serverspec'
set :backend, :exec
```
4. `cd ..`でRailsのプロジェクトディレクトリから出る。
5. `mkdir my_serverspec_tests`を実行する。`my_serverspec_tests`は新しく作成するディレクトリで任意の名前をつける。
6. `cd my_serverspec_tests`を実行する。
7. `serverspec-init`を実行する。
8. 今回はOSがAmazon Linux2のEC2にSSH接続してテストを実行したいので、`Select OS type`ではUN*Xである1を選択して、`Select a backend type`ではSSHである1を選択する。AWSを使用しているので`Vagrant instance`はnを選択し、`Input target host name`はホスト名またはIPアドレスを入力する。
9. `rspec --init`を実行する。
11. `my_serverspec_tests`ディレクトリの`spec`ディレクトリでテストを実行したいファイルを作成してコードを記述します。
12. Railsアプリのプロジェクトディレクトリで`rspec ../my_serverspec_tests`を実行する。このコマンドを実行することでテストコードの実行をプロジェクトディレクトリ外で行い、かつプロジェクトディレクトリ配下で設定した内容をテストできる。

※上記の11まで操作が行ったあとにUnicornを停止して再度起動しようとすると起動できなくなる。これを解決するにはGemfileの`gem 'serverspec'`を削除することで起動できるようになる。また、テストコードを実行したいときはGemfileの`gem 'serverspec'`を追加してあげる必要がある。
