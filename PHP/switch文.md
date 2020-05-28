# switch文  
* if文の方が読みやすののでif文を使った方がいい。  
* 処理を追えたら必ずbreak;を入れる。  
* ==が通常適用される。===を使用するなら変数を用いる
```
<?php
$data = 1;

switch($data) {
  case 1:
    echo '1です';
  break;
  case 2:
     echo '2です';
  break;
  case 3:
    echo '3です';
  break;
  default:
    echo '1-3ではありません';
}
?>
```
```
[変数を用いた場合]
<?php
$data = '1';

switch($data) {
  case $data === 1:
    echo '1です';
  break;
  case 2:
     echo '2です';
  break;
  case 3:
    echo '3です';
  break;
  default:
    echo '1-3ではありません';
}
?>
```
