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
15. GitHubで新しくリポジトリを作成する。パブリック、サブネットはどちらでもよい。
16. `git remote add origin [リポジトリのURL]`を実行する。
17. 
