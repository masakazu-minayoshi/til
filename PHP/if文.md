# if文  
```
<?php
//if文でデータが入っているかどうかも確認できる。
//isset, empty, is_null

$test = '1';
//空ではない時に条件を実行
if(!empty($test)) {
  echo '変数はからではありません';
}
// 三項演算子
//if else
//条件 ? 真：偽
$math = 80;
$comment = $math > 80 ? 'good' : 'not good';

echo $comment;

?>
```
