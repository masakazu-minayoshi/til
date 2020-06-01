# findメソッド  
* 全ての子孫要素(自分よりも下の階層の要素全て）の中から、指定したセレクタを持つ要素を取得したい時に用いる。  
下図の例では、<div id="wrapper">から</div>の中にあるすべての<a>要素を取得することができます。  
# childrenメソッド  
* 指定したセレクタが持つ子要素（一階層だけ下）の中から指定したセレクタに合致した要素を取得したい時に用いる。  
# コード例とイメージ  
```
[sample.html]
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Progate</title>
  <link rel="stylesheet" type="text/css" href="stylesheet.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
</head>
<body>
  <!-- "find-method"というidをつける-->
  <div class="btn" id ="find-method">findメソッド</div>
  <!-- "children-method"というidをつける -->
  <div class="btn" id ="children-method">childrenメソッド</div>
  <div id="wrapper">
    <a href="#">リンク1</a>
    <div>
      <a href="#">リンク2</a>
    </div>
  </div>

  <script src="script.js"></script>

</body>
</html>
```
```
[style.css]
.btn {
  display: inline-block;
  cursor: pointer;
  width: 180px;
  padding: 12px 0;
  background-color: #5dca88;
  box-shadow: 0px 5px #279C56;
  border-radius: 3px;
  color: #fff;
  font-size: 12px;
  margin-bottom: 20px;
  text-align: center;
}

.btn:active {
  position: relative;
  top: 5px;
  box-shadow: none;
}

#wrapper {
  margin-top: 30px;
}
```
```
[test.js]
$(function(){
//「#find-method」がクリックされた時に起こるイベントを設定する。
  $('#find-method').click(function(){
//findメソッドで「#wrapper」内のaタグの要素を取得しcssを変更させる。
    $('#wrapper').find('a').css('color', 'red');
  });
//「#children-method」がクリックされた時に起こるイベントを設定する。
  $('#children-method').click(function(){
//「#wrapper」の一階層下にある「a」要素を取得し、fadeOutメソッドで隠す処理を定義する。
    $('#wrapper').children('a').fadeOut;
  });
});
```
