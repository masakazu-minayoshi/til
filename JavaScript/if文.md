# if文  
* （例）合言葉を入力し正しければOK、間違っていればエラ〜メッセージが表示される条件文。  

```
<!DOCTYPE html>
<html>
  <head>
    <meta content ='ja'>
    <meta charset="UTF-8">
<title>JavaScript</title>
<!-- <link rel="stylesheet" href="reset.css">
<link rel="stylesheet" href="style.css"> -->

  </head>
  <body>
    <p>合言葉を入力して下さい</p>
    <p><input type="text" id="secretWord"></p>
    <p><button id="checkSecretWord">合言葉をチェックする！</button></p>

    <!-- JavaScriptのイベント -->
    <script type="text/javascript">
     document.getElementById("checkSecretWord").onclick = function(){
       var secretWordEntered = document.getElementById("secretWord").value;
       var secretWord = "スゲーナスゴイデス";
       
       if(secretWordEntered == secretWord) {
        alert("OK");
       } else {
         alert("正しい合言葉を入力して下さい");
       }
     }
    </script>
  </body>
</html>
```
