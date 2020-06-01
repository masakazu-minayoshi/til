# textメソッド  
* HTMLそのものを変更することができる。  
* textメソッドは、$('セレクタ').text('書き換える文字列');で記述する。  
# htmlメソッド  
* 要素の中身のHTMLを書き換えることができる。  
* htmlメソッドの引数は、単なる文字列ではなくHTML。  
# コード&イメージ図  
[![Image from Gyazo](https://i.gyazo.com/a7871d4de9405f9aaaa9d329a1932d19.gif)](https://gyazo.com/a7871d4de9405f9aaaa9d329a1932d19)
```
[sample.html]
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <link rel="stylesheet" href="style.css" />
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script> 
    </head>
  <body>
    <div>
      <!-- 文字を変更させるためにidを付与する -->
      <div class="btn" id="change-text">リベラルアーツ大学</div>
      <!-- HTMLの形態をURLに変更するためにidを付与する -->
      <div class="btn" id="change-html">ホームページに移動するならクリック</div>
      <!-- 変更させる文章 -->
      <h1 id="text">知識マッチョになるなら</h1>
    <script src="test.js"></script>
  </body>
</html>
```
```
[style.css]
.btn{
  display: inline-block;
  cursor: pointer;
  padding: 8px 30px;
  background-color: #5dca88;
  box-shadow: 0px 5px #279C56;
  border-radius: 3px;
  color: #fff;
  font-size: 10px;
}
.btn:active{
  position: relative;
  top: 5px;
  box-shadow: none;
}
```
```
[test.js]
$(function() {
  // 「#change-text」に対するclickイベントを定義
  $('#change-text').click(function(){
    // text要素ないを引数の文字列にを変更させるイベントを定義
    $('#text').text('リベラルアーツ大学');
  });
  //「#change-html」に対するclickイベントを定義
  $('#change-html').click(function(){
    // htmlの様式を変更させるイベントを定義
    //#text要素内を引数のHTMLで変更させる。
    $('#text').html('<a href="https://liberaluni.com/">リベラルアーツ大学</a>');
  });
});
```
