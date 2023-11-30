# 1つのサーバー内でServerspecのインストールからテストコードの実行まで
1.  `ec2-user`ディレクトリで`gem install serverspec`を実行する。
2. `mkdir [任意のディレクトリ名]`を実行する。
3. `cd [2で作成した任意のディレクトリ名]`を実行して移動する。
4. `serverspec-init`を実行する。
5. UN*XとExec (local)を選択する。今回は1つのサーバー内で完結するのでExec (local)を選択している。
6. `serverspec-init`で自動作成された`sample_spec.rb`をテストしたい内容のコードに書き換える。
7. 2で作成したテスト用のディレクトリで`rake spec`を実行する。

# Serverspecのテストコード

```
require 'spec_helper'

listen_port = 8080

describe package('nginx') do
  it { should be_installed }
end

describe port(listen_port) do
  it { should be_listening }
end

describe command('curl http://127.0.0.1:#{listen_port}/_plugin/head/ -o /dev/null -w "%{http_code}\n" -s') do
  its(:stdout) { should match /^200$/ }
end
```

## 解説
### `require 'spec_helper'`
テストコードのファイルに必ず記述しなければいけないもの。
### `describe package('nginx') do`
`package`は対象のパッケージがインストールされているかをテストするもの。今回は、Nginxがインストールされているかをテストしている。
### `describe port(listen_port) do`
`port`は対象のポートがリッスン状態であるかをテストするもの。今回は、8080番ポートがリッスン状態であるかをテストしている。
### `describe command('curl http://127.0.0.1:#{listen_port}/_plugin/head/ -o /dev/null -w "%{http_code}\n" -s') do`
`command`はカッコ内に書かれたコマンドを実行したあとの出力に対してテストするためのもの。今回は、HTTPリクエストの応答コードが200であるかをテストしている。`curl`コマンドはWebページやファイルをダウンロードするためのコマンドで`-o`と`-w`と`-s`はcurlコマンド専用のオプション。`-o /dev/null`によって`curl`コマンドの出力が全て削除されるが、`-w "%{http_code}\n`があるのでHTTPリクエストの応答コードのみを出力できるようにしている。`-s`はcurlコマンドを実行した際の進捗状況のメッセージを表示させないようにするオプション。
