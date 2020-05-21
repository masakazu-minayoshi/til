
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

    <div id="wankoSobas"></div>
   
    <!-- JavaScriptのイベント -->
    <script type="text/javascript">
        var wankoSobas = ["わんこそば","わんこそば","わんこそば","わんこそば","わんこそば","わんこそば"];
        var  wankoSobaInteger = "";
      
        var i =0;
        //配列の要素を数えるlengthを使用する。配列の数が増えても要素を取得するので数字を書き換えなくて済む。
        while(i < wankoSobas.length) {
          wankoSobaInteger =  wankoSobaInteger + "<p>" + wankoSobas[i] + "</p>";
          i++
        }
        document.getElementById("wankoSobas").innerHTML =  wankoSobaInteger;

    </script>
  </body>
</html>
```
