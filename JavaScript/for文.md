# for文  
* 入学式に参加する１年生の各組みを体育館に並んでもらう。

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

    <div id="classes"></div>
   
    <!-- JavaScriptのイベント -->
    <script type="text/javascript">
      // i++ インクルメンタル演算子
      // for(var i=5; i > 0; i-- ) {
      //   alert(i);
      // }
        var classes = ["1年１組","1年2組","1年3組","1年4組","1年5組"];
        var classString = "";
        // for(var i =0; i<4; i++) {
        //   alert(classes[i]);
        // }
        //配列の要素を数えるlengthを使用する。配列の数が増えても要素を取得するので数字を書き換えなくて済む。
         for(var i =0; i<classes.length; i++) {
          // alert(classes[i]);
          classString = classString + "<p>" + classes[i] + "</p>";
        }
        document.getElementById("classes").innerHTML = classString;

    </script>
  </body>
</html>
```
