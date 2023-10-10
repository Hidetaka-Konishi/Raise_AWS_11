# Serverspecのインストールからテストコードの実行まで
1. Gemfileに`gem 'serverspec'`を追加する。
2. `bundle`を実行する。
3. `serverspec-init`を実行する
4. 今回はOSがAmazon Linux2のEC2にSSH接続してテストを実行したいので、`Select OS type`ではUN*Xである1を選択して、Select a backend typeではSSHである1を選択する。
5. `sample_spec.rb`にテストコードを記述する。
6. `spec_helper.rb`ファイルの先頭に以下のコードを追加する。

```ruby
require 'serverspec'
set :backend, :exec
```
7. `rake spec`を実行する。テストを実行できなかった場合は引き続き8からの手順を行う。
8. `cd ..`でRailsのプロジェクトディレクトリから出る。
9. `mkdir my_serverspec_tests`を実行する。`my_serverspec_tests`は新しく作成するディレクトリで任意の名前をつける。
10. `cd my_serverspec_tests`を実行する。
11. git init`を実行する。
12. GitHubで新しくリポジトリを作成する。パブリック、サブネットはどちらでもよい。「Add a README file」にチェックを入れる。
13. `git remote add origin [リポジトリのURL]`を実行する。
14. `echo "# My Serverspec Tests" > README.md`を実行する。
15. `git add README.md`を実行する。
16. `git commit -m "任意のメッセージ"`を実行する。
17. `git push -u origin master`を実行する。
18. ユーザー名にはGitHubのユーザ名を入力する。
19. パスワードを生成するために、GitHubアカウントの右上のユーザーのマークから「Settings」をクリックする。
20. 左側のメニューから「Developer settings」をクリックする。
21. 「Personal access tokens」をクリックする。
22. 「Tokens(classic)」をクリックする。
23. 「Generate new token」→「Generate new token(classic)」をクリックする。
24. 「Note」に名前を入力して、「Select scopes」では「repo」にチェックを入れ、一番下までスクロールして、「Generate token」をクリックする。
25. トークンが表示されるのでコピーして大切に保管し、パスワード入力欄にコピーしたトークンを入力する。
26. 新しく作成したディレクトリで`touch Gemfile`を実行する。
27. Gemfileに以下のコードをコピーして貼り付けます。

```ruby
source 'https://rubygems.org'

gem 'serverspec'
gem 'rake'
```
28. `bundle install`を実行する。
29. `serverspec-init`を実行する。
30. `rspec --init`を実行する。
31. `spec/spec_helper.rb`ファイルの先頭に以下のコードを追加する

```ruby
require 'serverspec'
set :backend, :exec
```
32. `spec`ディレクトリでテストを実行したいファイルを作成してコードを記述します。
33. Railsアプリのプロジェクトディレクトリで`rspec ../my_serverspec_tests`を実行する。このコマンドを実行することでテストコードの実行をプロジェクトディレクトリ外で行い、かつプロジェクトディレクトリで設定した内容をテストできる。
