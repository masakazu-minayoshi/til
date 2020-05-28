# 文字列関数（str_replace)  
```
<?php

$text = 'abc';
//出力結果：3
echo strlen($text);

$text = 'あいうえお';
//出力結果：15
echo strlen($text);
//→日本語は UTF-8 3~6バイトだから。

//5と出力させるにはマルチバイトに適用させる
echo mb_strlen($text);
?>
```
> 引用
[マルチバイト文字列 関数](https://www.php.net/manual/ja/ref.mbstring.php)  
* 置換
```
<?php
$str = '文字列を置換します';
echo str_replace('置換','ちかん',$str);
?>
▶️出力結果：文字列をちかんします
```
> 引用
[str_replace](https://www.php.net/manual/ja/function.str-replace.php)
