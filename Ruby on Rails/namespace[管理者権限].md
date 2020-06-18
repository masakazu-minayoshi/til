# 問題.1     
Railsアプリで管理者ページを作ろうと考えています。  
通常コントローラーはapp/controllersフォルダに置きます。  
しかし、管理者機能用のコントローラーは、controllersフォルダに、<br>adminというフォルダを作成しその中にまとめた方が整理しやすいと考えました。  
この場合、Railsのある機能を使うと適切なルーティングを作成することができます。その機能の名前を答えてください。  
```
namespace（名前空間）あるいはmodule
```

# 問題.2  
上記の内容にしたがって、adminフォルダにproductsコントローラー（アクションはindexのみ）を作成します。  
その時のコントローラーおよびroutes.rbにどのような記述が必要か答えてください。

```
[products_controller.rb]
class Admin::ProductsController < ApplicationController
  def index
  end
end

[routes.rb]
  namespace :admin do
    resources :products, only: :index
  end

```


> 参考  
[【初心者向け】管理者ユーザーと管理者用controllerの追加方法[Ruby, Rails]](https://qiita.com/tanutanu/items/7ce8826615f1af605164)  
[gemを使わず管理画面を実装](https://haayaaa.hatenablog.com/entry/2019/02/11/155811)  
