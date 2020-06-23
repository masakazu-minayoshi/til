## RailsアプリケーションでのCSS、 SCSSのインポートに関する問題   
requireと@importはどう違うのか、それぞれのインポートの仕組みを踏まえて答えてください。
* rails newを実行しアプリケーションを作成した段階では、  
application.cssに *= require_tree .という記述があり、これによってCSSファイルを読み込んでいる。  
* SCSSを使用する際は、ファイルの拡張子をscssに変更した上で、@importでファイルを読み込みをしている。  
## 回答  
### require  
* requireはRailsのアセットパイプラインの仕組みを使ってファイルをインポートする。  
* アセットパイプラインは、cssファイルやJavaScriptのファイルを１つにまとめ、<br>圧縮することで処理速度を早くするための仕組み。  
* sprocketsというgemがアセットパイプラインの機能を担っている。
### @import  
* @importはscssが用意しているメソッド。  
* application.scssと拡張子を変更しないと使えない。  
* application.scssからscssファイルをインポートするために使用する。
