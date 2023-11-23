# 1つのサーバー内でServerspecのインストールからテストコードの実行まで
1.  `ec2-user`ディレクトリで`gem install serverspec`を実行する。
2. `mkdir [任意のディレクトリ名]`を実行する。
3. `cd [2で作成した任意のディレクトリ名]`を実行して移動する。
4. `serverspec-init`を実行する。
5. UN*XとExec (local)を選択する。今回は1つのサーバー内で完結するのでExec (local)を選択している。
6. `serverspec-init`で自動作成された`sample_spec.rb`をテストしたい内容のコードに書き換える。
7. 2で作成したテスト用のディレクトリで`rake spec`を実行する。
