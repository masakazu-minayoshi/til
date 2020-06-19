# 問題  
showアクションの中にあるarticleという変数定義ですが、このままだとビューの表示を意図した通りに行うことができません。<br>その理由と解決策を解説してください。
```
class ArticlesController < ApplicationController

  def show
    article = Article.find(params[:id])
  end
end
```
[回答]  
Railsではコントローラで設定された「インスタンス変数」がビューに渡される仕組みになっている。  
コードのarticleは通常のローカル変数であるためビューで使うことができないので、articleを@articleに変更すればよい。  
