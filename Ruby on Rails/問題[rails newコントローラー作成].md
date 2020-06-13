# 問題  
下記の仕様に従って、Railsアプリケーションの雛形を作成してください。  
・アプリケーション名は任意。  
・データベースはMySQLを使用する。  
・tweetsコントローラー内に、index, new, createアクションがある（メソッドの中身が記述してある必要はありません）。  
・コントローラーに対応したビューファイルがある（表示される内容はデフォルトのままで構いません）。  
・tweetモデル内に、title, contentカラムがある（いずれも文字列）。  
・tweetsテーブルが作成されている。  
・必要なルーティングが設定されている。  
※ただし、scaffoldを使用してはいけません。  

```
# -d mysqlでデータベースをMySQLに指定
> rails _4.2.6_ new sample-app -d mysql
# index,new,createアクションがあるtweetsコントローラーを作成
> rails g controller tweets index new create
# データベース作成
> bundle exec rake db:create
string型のtitleとcontentカラムを作成
> rails g model tweet title:string content string
# migrationファイルを作成
> bundle exec rake db:migrate
# index,new,createのルーティングを設定
> routes.rb に resources :tweets, only: [:index, :new, :create] を追加し、不要な記述を削除
```
