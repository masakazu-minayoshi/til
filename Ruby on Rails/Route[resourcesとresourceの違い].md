# 問題  
routes.rbでは、resourcesを使ってルーティングを定義することができる。  
resourcesの代わりにresourceを使ってルーティングを定義することもできる。  
resourceを利用した際に生成されるルーティングについて、resourcesを用いた場合との主な違いを2点、説明してください。

[回答]
* resourcesメソッド
Railsの基本となるコントローラの7つのアクション名に対してのルーティングを自動で生成するメソッド。

* resourceメソッド  
・idつきのパスが生成されない。show, editアクションの実行に、idが必要ない場合に有効。  
・indexアクション用のルーティングが生成されない。  

```
[routes.eb]
resource :users

[生成されるルーティング]
 new_users GET    /users/new(.:format)  users#new
edit_users GET    /users/edit(.:format) users#edit
     users GET    /users(.:format)      users#show
           PATCH  /users(.:format)      users#update
           PUT    /users(.:format)      users#update
           DELETE /users(.:format)      users#destroy
           POST   /users(.:format)      users#create


```

> 参考  
[resourcesとresourceの違いについて！](https://qiita.com/wacker8818/items/1ba526fcbc73e065a511)  
