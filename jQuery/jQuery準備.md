# jQueryの読み込み  
* jQueryを使用するには、jQueryライブラリを読み込む必要があり、インターネット経由で読み込むのが一般的。  
* <head>タグの中で下図のようにURLを読み込むことで、jQueryを使うことができる。  
```
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <link rel="stylesheet" href="style.css" />
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script> 
    </head>
```
* jQueryは、.js形式のファイルにコードを書く。  
* HTMLファイルで、<script src="ファイルのURL"></script>と書くことで、<br>jQueryのコードを記述するファイルが読み込まれる。  
* <script>はCSSファイルの読み込みのように<head>タグの中にも書けるが、<br></body>の直前に書くことで、WEBページの表示速度をより早くすることができる。   
```
[….html]
 <script src="test.js"></script>
</body>
</html>
```
# jQueryの型  
* jQueryはHTMLの中身を操作するため、HTMLの読み込みが完了してからjQueryによる操作を開始するようにする。  
そのためにはreadyイベントを使用し、$(document).ready()の中身にjQueryの処理を書くが、<br> この構文には省略形も用意されており、$(function(){ });と書くことも出来ます。  
```
[jQueryの基本的な型]
//「.ready」でHTMLの読み込みが完了したらjQueryを実行する。
$(document).ready(function(){
  //jQueryの処理を書く
});

[readyイベントの省略]
$(function(){
  //jQueryの処理を書く
});
```
