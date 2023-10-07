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
11. `rvm use 3.1.2@my_new_gemset --create`を実行する。3.1.2は実際に使用しているrubyのバージョンに合わせる。これにより`my_new_gemset`という名前のGemsetが作成される。
12. `gem install bundler`を実行する。
13. `gem install serverspec`を実行する。
14. `bundle install`を実行する。
15. `find ./spec -type f -name '*_spec.rb'`を実行して

11. `cd ..`でRailsのプロジェクトディレクトリから出る。
12. `mkdir my_serverspec_tests`を実行する。
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
29. 
