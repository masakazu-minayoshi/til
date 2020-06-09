# ActiveRecordとは？  
* ・Ruby on Railsで採用されているOR Mapperのこと。    
※ORMとは、直接SQL文を書く代わりに非常に短いコードでデータベースの読み書きを行える機能のこと。<br>OR Mapperとは、そのためのモジュールのこと。
* モデルとテーブルをつなぎ合わせることでRailsからテーブルのレコードにアクセスできるようにする役割がある。
* Railsにデフォルトでインストールされており、実際に利用する際には、<br>ActiveRecord::Baseというクラスを継承して使用する。

# ActiveRecord::Baseメソッドとは?  
* ActiveRecord::Baseで定義されている「テーブルにアクセスして情報を取得するためのメソッド」のこと。  
* モデルクラスはこのActiveRecord::Baseというクラスを継承しているが、<br>クラスを継承した場合は継承元のクラス（親クラス）で定義されているメソッドを利用することができる。  
→そのため、モデルクラスはActiveRecord::Baseメソッドを用いて、テーブルにアクセスし情報を取得することができる。  
(例)rails g model tweetのコマンドを実行すると、<br>ActiveRecord::Baseを継承しモデルTweetクラスが作成される。<br>そのため、Tweetクラスのインスタンスに対して、ActiveRecord::Baseで定義されているメソッドを使うことができる。

```
（例）app/models/tweet.rb
class Tweet < ActiveRecord::Base   
end
```



> 参考
[Rails: ActiveRecord::Baseメソッドのまとめ](https://qiita.com/penguin_note/items/adb0b9bf7c13c1b1d44d)  
