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
9. 
