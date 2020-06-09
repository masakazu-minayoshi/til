# ORM機能とは、(オブジェクト/リレーショナルマッピング)  
* 直接SQL文を書く代わりに非常に短いコードで、データベースの読み書きを行える機能。  
* RailsではActiveRecordというモジュールで実装されている。  
> 参考  
[Active Record の基礎](https://railsguides.jp/active_record_basics.html)  
[RailsのORM機能について](https://qiita.com/okamoto_ryo/items/54d6a3b5d879aeee5b39)  
# database.ymlファイル  
*(what?):複雑なデータ構造をシンプルに表現するファイル形式  
* 役割  
・rake db:createのコマンドを実行した時に作成されるデータベースの名称を指定する。  
・RailsアプリケーションがSQLサーバーにアクセスするときのソケットファイルの位置を指定する。  
# アソシエーション 
* DBのテーブルとテーブルを紐づけることによって、関連するデータの読み書きを容易にするための機能。  

> 参考
[【YAML】Railsのdatabase.ymlについてなんとなく分かった気になっていた記法・意味まとめ](https://qiita.com/terufumi1122/items/b5678bae891ba9cf1e57)
