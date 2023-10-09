# Serverspecのインストールから実行まで
1. Gemfileに`gem 'serverspec'`を追加する。
2. `bundle`を実行する。
3. `serverspec-init`を実行する
4. 今回はOSがAmazon Linux2のEC2にSSH接続してテストを実行したいので、`Select OS type`ではUN*Xである1を選択して、Select a backend typeではSSHである1を選択する。
5. `sample_spec.rb`にテストコードを記述する。
6. `bin/rails db:environment:set RAILS_ENV=test`を実行する。
7. `spec_helper.rb`ファイルの先頭に以下のコードを追加する。

```ruby
require 'serverspec'
set :backend, :exec
```
8. テストコードを書いたファイルで先頭の部分に`require 'spec_helper'`が記述されていることを確認する。
9. NginxとUnicornを再起動する。Unicornが再起動できない場合は11からの手順を行う。
10. `rake spec`を実行する。
11. `cd ..`でRailsのプロジェクトディレクトリから出る。
12. `mkdir my_serverspec_tests`を実行する。`my_serverspec_tests`は新しく作成するディレクトリで任意の名前をつける。
13. `cd my_serverspec_tests`を実行する。
14. `git init`を実行する。
15. GitHubで新しくリポジトリを作成する。パブリック、サブネットはどちらでもよい。「Add a README file」にチェックを入れる。
16. `git remote add origin [リポジトリのURL]`を実行する。
17. `echo "# My Serverspec Tests" > README.md`を実行する。
18. `git add README.md`を実行する。
19. `git commit -m "任意のメッセージ"`を実行する。
20. `git push -u origin master`を実行する。
21. ユーザー名にはGitHubのユーザ名を入力する。
22. パスワードを生成するために、GitHubアカウントの右上のユーザーのマークから「Settings」をクリックする。
23. 左側のメニューから「Developer settings」をクリックする。
24. 「Personal access tokens」をクリックする。
25. 「Tokens(classic)」をクリックする。
26. 「Generate new token」→「Generate new token(classic)」をクリックする。
27. 「Note」に名前を入力して、「Select scopes」では「repo」にチェックを入れ、一番下までスクロールして、「Generate token」をクリックする。
28. トークンが表示されるのでコピーして大切に保管し、パスワード入力欄にコピーしたトークンを入力する。
29. 新しく作成したディレクトリで`touch Gemfile`を実行する。
30. Gemfileに以下のコードをコピーして貼り付けます。

```ruby
source 'https://rubygems.org'

gem 'serverspec'
gem 'rake'
```
31. `bundle install`を実行する。
32. `serverspec-init`を実行する。
33. `rspec --init`を実行する。
34. `spec/spec_helper.rb`ファイルの先頭に以下のコードを追加する

```ruby
require 'serverspec'
set :backend, :exec
```
35. `spec`ディレクトリでテストを実行したいファイルを作成してコードを記述します。
36. Railsアプリのプロジェクトディレクトリで`rspec ../my_serverspec_tests`を実行する。このコマンドを実行することでテストコードの実行をプロジェクトディレクトリ外で行い、かつプロジェクトディレクトリで設定した内容をテストできる。
