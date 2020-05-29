# form(GET,POST)  
* GETとPOSTそれぞれ連想配列の形でデータを取得できる。
[![Image from Gyazo](https://i.gyazo.com/474e3bb1e3b6444919014fb167d9b0de.png)](https://gyazo.com/474e3bb1e3b6444919014fb167d9b0de)
```
<?php
//$_GET:スーパーグローバル変数
//連想配列でデータを取得（下記だたnameがkyeで入力値がvalue)
echo '<pre>';
var_dump($_GET);
echo '</pre>';

?>


<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <form method="GET" action="input.php">
  名前
    <input type="text" name="name">
    <br>
    <input type="checkbox" name="sports[]" value="野球">野球
    <input type="checkbox" name="sports[]" value="サッカー">サッカー
    <input type="checkbox" name="sports[]" value="バスケ">バスケ

    <input type="submit" value="送信">
  </form>
</body>
</html>

```
