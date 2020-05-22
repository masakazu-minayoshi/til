# hoverイベント  
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

