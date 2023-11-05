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
