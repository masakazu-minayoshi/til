# Active Record コールバック  
## コールバックとは?  
* オブジェクトの生成(create)・更新(update)・削除(delete)のタイミングで呼び出されるメソッド。  
バリデーションを実行する時の前後に共通の処理を追加する仕組み。  
* イベント（create, save,destroy）をトリガーとして登録可能。  
## メリット  
* トリガに対してメソッドを共通化できて便利。
* モデルで指定し処理を共通化することで、モデルの一貫性を保ちつつコード量を減らすことができる。  


# 問題  
Railsのコールバックを利用して以下の機能を実装してください。  
①Pictweetに機能を追加する。  
②ユーザーが投稿を行ったら、textカラムに保存されるデータの最後に「！！」を自動で追加する。  
①と②の変更内容を記載しなさい.  

```
tweet.rb
（変更点のみ記載）
  before_create :change_tweet

  def change_tweet
    self.text = text + "！！"
  end

end
```
## [補足]
* 上記コードのselfには、これから保存されるTweetクラスのインスタンスが代入される。  
そのため、self.textとするとユーザーが入力した投稿のtextを取得することができる。  
* 通常この場合のselfは省略可能なので```self.text = self.text + "！！"```と右辺のselfは書かなくても大丈夫。  
しかし、その例外としてセッターメソッドを使う場合のselfは省略できないため、左辺のselfは必須となる。  

## 処理の流れ  
①before_createが作動。    

②change_tweetメソッドが呼び出される。  
  
③change_tweetメソッドの中に定義してあるself.textの処理。    

④self.textの中には、text + "！"という処理が代入されている。  

⑤textとは、Tweetクラスのインスタンスである。  

* textとは、ユーザーが投稿ツイート内容のことを意味している。  
+ "！"の記述により、text の最後に"！！"を加える処理が加えて行われる。




> 参照  
[Active Record コールバック](https://railsguides.jp/active_record_callbacks.html)  
[ActiveRecordのコールバック早見表 | Rails](https://morizyun.github.io/ruby/active-record-callback.html)  
[Railsのコールバックを用いてtextカラムに自動で記述を追加する方法](https://qiita.com/zetawork/items/12d3549812d3f6cf06d6)  
[Rails コールバックのbefore_createについて](https://qiita.com/okamoto_ryo/items/458097542e826623b7ad)  




