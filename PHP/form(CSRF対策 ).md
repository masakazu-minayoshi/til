# CSRF対策    
* session_start();で対応。  
```
<?php
//CSRF対策
session_start();
//クリックジャッキング対策
header("X-FRAME-OPTIONS: DENY");
//XSS(Cross-Site Scripting)対策
function h($str)
{
  return htmlspecialchars($str, ENT_QUOTES, 'UTF-8');
}

echo'<pre>';
var_dump($_SESSION);
echo'</pre>';

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


<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

  <?php if($pageFlag === 1) : ?>
<!-- //合言葉があっているかの条件で確認する。 -->
<?php if($_POST['csrf'] === $_SESSION['csrfToken']): ?>

  <form method="POST" action="input.php">
  名前
  <?php echo h($_POST['your_name']) ; ?>
  <br>
  メールアドレス
  <?php echo h($_POST['email']) ; ?>
  <input type="submit" name="back" value="戻る">
  <input type="submit" name="btn_submit" value="送信する">
  <!-- GETやPOSTで1回通信をするとデータが消えるのでhiddenで受け渡す。 -->
  <input type="hidden" name="your_name" value="<?php echo h($_POST['your_name']);?>">
    <input type="hidden" name="email" value="<?php echo h($_POST['email']);?>">
    <input type="hidden" name="csrf" value="<?php echo $token ?>">
  </form>
  <?php endif; ?>
  <?php endif; ?>

  <?php if($pageFlag === 2) : ?>
  <!-- //合言葉があっているかの条件で確認する。 -->
  <?php if($_POST['csrf'] === $_SESSION['csrfToken']) : ?>
    送信が完了しました
<!-- 合言葉が残っているとセキュリティ上問題があるので削除する。 -->
    <?php unset($_SESSION['csrfToken']); ?>
  <?php endif; ?>
  <?php endif; ?>

  <?php if($pageFlag === 0) : ?>
  <?php
  //CSRF対策
  //$SESSIONにcsrfTokenがセットされていなかったら
  if(!isset($_SESSION['csrfToken'])) {
  // bin2hexで16進数に変換し$csrfTokenに代入
  $csrfToken = bin2hex(random_bytes(32));
  //$csrfTokenを$_SESSION['csrfToken']に代入
  $_SESSION['csrfToken'] = $csrfToken;
  }
  //既に設定されていたら$tokenに$_SESSION['csrfToken']を代入
  $token = $_SESSION['csrfToken'];
  ?>
  <form method="POST" action="input.php">
  名前
  <input type="text" name="your_name" value="<?php echo h($_POST['your_name']) ; ?>">
  <br>
  メールアドレス
  <input type="email" name="email" value="<?php echo h($_POST['email']) ; ?>">
  <input type="submit" name="btn_confirm" value="確認する">
  <input type="hidden" name="csrf" value="<?php echo $token; ?>">
  </form>
  <?php endif; ?>
</body>
</html>
```
> 引用
[PHPドキュメント：random_bytes](https://github.com/masakazu-minayoshi/til/new/master/PHP)


