# layoutメソッド  
## layoutメソッドとは?  
* コントローラによってヘッダー・フッターのデザインを変更したり、読み込むCSSを切り替えるメソッド。  
* layoutメソッドに指定するファイルは、/app/views/layoutsフォルダに作成する。  


```
[コントローラー | 記述の仕方]
layout 'ファイル名'
```
```
[コントローラー | layoutメソッドの使用例]
class コントローラ名 < ApplicationController
  # layoutを指定した場合、layouts/application.html.erbではなくlayouts/top.html.erbが読み込まれる
  layout 'top'

  def アクション名
  end

end
```
○上記のコードの場合  
指定したコントローラのアクションが呼び出された際のレイアウトファイルとして、<br>app/views/layouts/top.html.erbが使われるようになる！  

○上記のコードからlayout 'top'を抜いた場合  
指定したコントローラのアクションが呼び出された際のレイアウトファイルとして、<br>app/views/layouts/layouts/top.html.erbが読み込まれる!  

> 参考  
[layoutメソッドについてまとめる！](https://qiita.com/wacker8818/items/49a7f6ca3086c38a2d9d)  
[【Rails】layoutメソッドの使い方をマスターしよう！](https://pikawaka.com/rails/layout)  

