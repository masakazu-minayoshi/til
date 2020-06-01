# hoverイベント  
* 要素にマウスが乗った時、外れた時に指定した処理を行うイベントです。  
* $('セレクタ').hover(マウスをのせた時の処理, マウスをはずした時の処理);と書く。  
* **引数を2つ必要で、引数の間はコンマで区切る**。  
(例①)iframeが変わる。  
[![Image from Gyazo](https://i.gyazo.com/7f0acfe331e3acc9b2ab247f5d180881.gif)](https://gyazo.com/7f0acfe331e3acc9b2ab247f5d180881)
```
<!DOCTYPE html>
<html>
    <head>
        <style type="text/css">
            #circle {
              width: 150px;
              height: 150px;
              border-radius: 50%;
              margin: 10px;
              background-color: green;
            }
            .iframe {
              width: 100%;
              height: 400px;
            }
        </style>
    </head>
    <body>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js">
</script> 
    <div id="circle"></div>
    <iframe src="https://techacademy.jp/magazine/36" class="iframe" ></iframe>
    <script type="text/javascript">
      $("div").hover (function(){
        $("iframe").attr("src","https://schoo.jp/");
      });
    </script>
    </body>
</html>
```
* 例②コード＆イメージ  
[![Image from Gyazo](https://i.gyazo.com/afa88c69308011e57c401feef86e8837.gif)](https://gyazo.com/afa88c69308011e57c401feef86e8837)
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
  <div id="bookkeeping-wrapper">
    <h1 class="bookkeeping-title">自己資本利益率(ROI:Return On Equity)とは？</h1>
    <p class="bookkeeping-text">
      自己資本(≒純資産)からどれだけ利益をあげたかを表す指標
      <br>
      →高ければ高いほど効率的に利益を稼いでいる。
      <br>
      ROE(%) = 当期純利益/純資産 → 15/150 = 10%
    </p>
  </div>
  <script src="test.js"></script>
</body>
</html>
```
```
[style.css]
/* hoverイベントで文章を表示させるために、
「.language-text」のCSSをdisplayプロパティで非表示にする */
.bookkeeping-text {
  display: none;
}
```
```
[test.js]
$(function(){
//「#bookkeeping-wrapper」にhoverした時のイベントを作成。
  $('#bookkeeping-wrapper').hover(
    function(){
//「.bookkeeping-text」にhoverした時のfadeInイベントを作成しカンマで区切る。
      $('.bookkeeping-text').fadeIn();
    },
//「.bookkeeping-text」からhoverが外れた時にfadeOutするイベントを作成。
    function(){
      $('.bookkeeping-text').fadeOut();
    }
  )
});
```

