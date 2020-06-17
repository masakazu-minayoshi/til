# 問題  
このアプリケーションでは商品の名前と価格を登録することができる。  
商品の新規作成が行われた場合、ユーザーが入力した価格に対して自動で消費税額8%を加算してからデータベースに保存させる。  
```
最初に、下記の手順でアプリケーションの雛形を作成してください。
> cd ~/フォルダ名/ 
> rails new model-app -d mysql
> cd model-app/
> rails g scaffold product name:string price:integer
> bundle exec rake db:create
> bundle exec rake db:migrate
```

①product.rbにメソッドadd_taxを追加してください。このメソッド内で、ユーザーの入力値に8%を加算してください。  
```
class Product < ApplicationRecord
  def add_tax
    self.price = (price * 1.08).round
   end
end
```
②上記の条件メソッドを使用し、上の条件を満たすようコードを書き換えてください。  

```
  def create
    @product = Product.new(product_params)
    @product.add_tax

    respond_to do |format|
      if @product.save
        format.html { redirect_to @product, notice: 'Product was successfully created.' }
        format.json { render :show, status: :created, location: @product }
      else
        format.html { render :new }
        format.json { render json: @product.errors, status: :unprocessable_entity }
      end
    end
  end
（3行目を追加）
```

* ユーザーが入力した価格に自動で消費税額8%を加算してからデータベースに保存することができる。  
→モデルのファイル内にメソッドを記述することで、モデルクラスのインスタンスに対してメソッドを追加できるから。  
この場合、product.rbにメソッドを書けば、Productクラスのインスタンスである@productに対して、<br>@product.add_taxの様にメソッドを使うことができる。
