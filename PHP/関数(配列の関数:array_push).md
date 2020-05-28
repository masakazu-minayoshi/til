# 配列の関数(array_push)  
* 配列に配列を使いする  
```
<?php

$array = ['りんご','みかん'];

array_push($array,'ぶどう','なし');
echo '<pre>';
var_dump($array);
echo '</pre>';
?>
▶️出力結果：
array(4) {
  [0]=>
  string(9) "りんご"
  [1]=>
  string(9) "みかん"
  [2]=>
  string(9) "ぶどう"
  [3]=>
  string(6) "なし"
}
```


> 引用  
[図解でわかるPHP配列関数一覧](http://html2php.starrypages.net/php/array-funcs)  
[PHPマニュアル：配列](https://www.php.net/manual/ja/language.types.array.php)  
