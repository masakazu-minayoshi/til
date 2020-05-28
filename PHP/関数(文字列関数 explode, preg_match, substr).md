# 文字列関数(explode, preg_match, substr)  
* 指定文字列で分割  
```
<?php
$str = '指定文字列で、分割します';

echo '<pre>';
var_dump(explode('、', $str));
echo '</pre>';
?>
▶️出力結果：
array(2) {
  [0]=>
  string(18) "指定文字列で"
  [1]=>
  string(15) "分割します"
}
```
> 引用
[explode](https://www.php.net/manual/ja/function.explode)  
* implode 文字列を結合させる。 (正規表現で用いる) 
```
<?php
$str = '特定の文字列が含まれるか確認する';
echo preg_match('/文字列/', $str);
?>
▶️出力結果：1
```
* 指定文字列から文字列を取得（返す）する  
```
<?php
echo substr('abcde', 1);
▶️出力結果：bcde
//マルチバイトで出力
echo mb_substr('かきくけこ', 2);
▶️出力結果：くけこ
?>

```
> 引用
[substr](https://www.php.net/manual/en/function.substr)

