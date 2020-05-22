# Droppable
(例①)ドラックしてドロップするとドロップしたエリアの文字が変わる。  
[![Image from Gyazo](https://i.gyazo.com/0939660288b0aae184cfc3b2149ba806.gif)](https://gyazo.com/0939660288b0aae184cfc3b2149ba806)
```
<!DOCTYPE html>
<html>
    <head>
      <link href="jquery-ui/jquery-ui.css" rel="stylesheet">
        <style>
          #drag { 
              width: 100px;
              height: 100px;
              background-color: aqua;
              margin: 20px;
          }
          #drop { 
              width: 400px;
              height: 200px;
              background-color: orange;
          }
        </style>
    </head>
    <body>
      <div id="drag">
          dragするよ
      </div>
      <div id="drop">
          <p>ここにドロップして下さい</p>
      </div>
      <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
      <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
    <script type="text/javascript">
    $("#drag").draggable();
      $("#drop").droppable({
        drop:function(event,ui){
            $(this)
            .addClass("ui-state-highlight")
            .find("p").html("ドロップされましたよ！");
        }
    });
    </script>
  </body>
</html>
```
> 引用
[StackTrace](http://stacktrace.jp/jquery/ui/interaction/droppable.html)  
> 引用
[jQuery-ui](https://jqueryui.com/droppable/)  
