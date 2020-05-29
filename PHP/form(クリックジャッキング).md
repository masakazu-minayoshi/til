# クリックジャッキング  
* PHPの上部に追加  
```
<?php
//クリックジャッキング対策
header("X-FRAME-OPTIONS: DENY");
//XSS(Cross-Site Scripting)対策
function h($str)
{
  return htmlspecialchars($str, ENT_QUOTES, 'UTF-8');
}

// echo'<pre>';
// var_dump($_POST);
// echo'</pre>';

$pageFlag =0;
//'btn_confirm'が空でなかったら条件実行。
if(!empty($_POST['btn_confirm'])) {
  $pageFlag = 1;
}
//'btn_submit'が空でなかったら条件実行。
if(!empty($_POST['btn_submit'])) {
  $pageFlag = 2;
}
?>
```
> 引用
[PHP脆弱性対応：クリックジャッキング攻撃への対応](https://deep-blog.jp/engineer/9514/)  
