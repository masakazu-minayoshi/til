# this  
イベントが発生した要素を取得する。  
# イメージ&コード例  
[![Image from Gyazo](https://i.gyazo.com/b3485f01688663163d89364e7778a3e7.gif)](https://gyazo.com/b3485f01688663163d89364e7778a3e7)
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
    <ul>
      <!-- <li>タグに"list-item"というclassをつける -->
      <li class="list-item">カツ丼</li>
      <li class="list-item">海鮮丼</li>
      <li class="list-item">ステーキ丼</li>
    </ul>
    <script src="test.js"></script>
  </body>
</html>
```
```
[style.css]
li {
  cursor: pointer;
}
```
```
[tes.js]
$(function(){
//「.list-item」要素に対するclickイベントを作成。
  $('.list-item').click(function(){
    //thisで要素を取得して処理を実行する。
    $(this).css('color','red');
  });
});
```
