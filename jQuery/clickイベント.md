# クリックイベントの例  
（例①) 丸と四角それぞれクリックするとアラートが表示される。<br>アラートを統一する時はdivを取得要素にする。  
[![Image from Gyazo](https://i.gyazo.com/832a627ea602e2a146b3d655d9472495.gif)](https://gyazo.com/832a627ea602e2a146b3d655d9472495)
```
<!DOCTYPE html>
<html>
    <head>
        <style type="text/css">
            #circle {
              width: 150px;
              height: 150px;
              border-radius: 50%;
              margin: 100px 200px 50px;
              background-color: green;
            }
            .square {
              width: 150px;
              height: 150px;
              margin: 50px 200px;
              background-color: red;
            }      
        </style>
    </head>
    <body>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script> 
    <div id="circle"></div>
    <div class="square"></div>
    <div class="square"></div>
    <script type="text/javascript">
        //jQueryの記述方法
        $("#circle").click (function(){
            alert("円がクリックされました。");
        })
        $(".square").click (function(){
            alert("四角がクリックされました。");
        })
    </script>
    </body>
</html>
```

（例②) 丸をクリックすると文字が変わる。  
[![Image from Gyazo](https://i.gyazo.com/86530bcd3af69f96e586ff61f5f495d6.gif)](https://gyazo.com/86530bcd3af69f96e586ff61f5f495d6)

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
        </style>
    </head>
    <body>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js">
</script> 
    <div id="circle"></div>
    <p>こんにちは</p>
    <script type="text/javascript">
      $("div").click (function(){
        $("p").html("円がクリックされました！");
      });
    </script>
    </body>
</html>
```

(例③)クリックするとiframeの内容が変わる。<br>iframeをimageにすると画像を差し替えることができる。    
[![Image from Gyazo](https://i.gyazo.com/6514ea9acc4dc7d003e4aee224d48c93.gif)](https://gyazo.com/6514ea9acc4dc7d003e4aee224d48c93)
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
      $("div").click (function(){
        $("iframe").attr("src","https://schoo.jp/");
      });
    </script>
    </body>
</html>
```
