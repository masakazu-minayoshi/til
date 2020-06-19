# 問題  
以下のようなコントローラがあるとします。  
4行目のArticle.find(params[:id])という記述のうち、params[:id]には詳細表示されたいレコードのidが格納されます。  
なぜそのような動作になるのか、「rails routes」という言葉を使って説明してください。

```
class ArticlesController < ApplicationController

  def show
    @article = Article.find(params[:id])
  end
end
```

[回答]  
rails routesを使ってアプリケーションのルーティングを確認すると、通常showアクションには以下のような設定がされている。

```
Prefix Verb   URI Pattern             Controller#Action
tweet  GET    /tweets/:id(.:format)   tweets#show
```
そのため、例えば「localhost:3000/tweets/3」というURLが指定されると、paramsの「:id」というキーのバリューとして「3」が代入される。  
そのため、そのあと呼び出されたコントローラー内でparams[:id]と取り出すことができる。  

> 参考  
[Railsガイド：Rails のルーティング](https://railsguides.jp/routing.html)  
[Model.find(params[:id]) を丁寧に調べた（Rails入門）](https://qiita.com/ryosuketter/items/44005785f47136a83ae1)  
[[Rails]params[:id]に値を渡す](https://qiita.com/yamamoto_shuji/items/8b4d139c6439ec57a9bb)
