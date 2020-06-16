# 問題
Railsを使わずにHTML, CSSでサイトを作成する際は、<br>HTMLファイルからlinkタグを使ってCSSファイルを読み込む設定を記述します。  
しかし、Railsの場合各ビューでCSSの読み込みの設定を書く必要はありません。  
①なぜ必要なCSSやJavaScriptが読み込まれるのか、<br>「アセットパイプライン」「Sprockets」「マニフェストファイル」という用語を用いて説明してください。

```
Railsにはアセットパイプラインという仕組みが用意されており、複数のCSSやJavaScriptファイルは一つにまとめて圧縮される。
この機能はSprocketsというGemが担っている。
各ビューが表示される際、必ずapplication.html.erbが読み込まれるが、
その中にstylesheet_link_tagの記述があり、それによってapp/assets/stylesheets/application.cssが呼び出される。
application.cssはマニフェストファイルといわれ、このファイルから各CSSファイルを呼び出す仕組みになっている。

```
②①を踏まえると、作成したCSSやJavaScriptのファイルはどこに配置すれば良いか説明してください。

```
cssの場合
app/assets/stylesheets のフォルダにファイルを置く。

JavaScriptの場合
app/assets/javaScripts のフォルダに置く
```

> 参考  
[公式ドキュメント:アセットパイプライン](https://railsguides.jp/asset_pipeline.html)  
[アセットパイプライン](https://qiita.com/krppppp/items/666d864e703a270fc8b6)  
[railsのアセットパイプラインについて解説する](https://qiita.com/hogehoge1234/items/9a94ebc93c5f937502cd)  
