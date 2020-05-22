# fadeIn&fadeOut  
[![Image from Gyazo](https://i.gyazo.com/f97e677d7f75f31915a307bdc52c3fbd.gif)](https://gyazo.com/f97e677d7f75f31915a307bdc52c3fbd)
```
<!DOCTYPE html>
<html>
    <head>
        <style type="text/css">
            #fadeInText {
                display: none;
            }
        </style>
    </head>
    <body>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
        <p id="text">このテキストは反転します</p>
        <button id="button">クリックする</button>

    <script type="text/javascript">
        $("#button").click(function(){
          //txetのcssがnone、つまり非表示だったら
          if($("#text").css("display") == "none"){
            //テキストをfadeIn（表示）させる。
            $("#text").fadeIn("slow");
          } else {
            //テキストをfadeOut（非表示）させる。
            $("#text").fadeOut("slow");
          }
        })
    </script>
    </body>
</html>

```
