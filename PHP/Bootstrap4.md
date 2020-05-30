# Bootstrap  
```
<?php
//CSRF対策
session_start();
//バリデーションのファイルを読み込む
require 'validation.php';
//クリックジャッキング対策
header("X-FRAME-OPTIONS: DENY");
//XSS(Cross-Site Scripting)対策
function h($str)
{
  return htmlspecialchars($str, ENT_QUOTES, 'UTF-8');
}

echo'<pre>';
var_dump($_POST);
echo'</pre>';

$pageFlag =0;
$error = validation($_POST);
//'btn_confirm'とエラ〜メッセージが空でなかったら条件実行。
if(!empty($_POST['btn_confirm']) && empty($error)) {
  $pageFlag = 1;
}
//'btn_submit'が空でなかったら条件実行。
if(!empty($_POST['btn_submit'])) {
  $pageFlag = 2;
}
?>


<!doctype html>
<html lang="ja">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
<body>

  <?php if($pageFlag === 1) : ?>
<!-- //合言葉があっているかの条件で確認する。 -->
<?php if($_POST['csrf'] === $_SESSION['csrfToken']): ?>

  <form method="POST" action="input.php">
  氏名
  <?php echo h($_POST['your_name']) ; ?>
  <br>
  メールアドレス
  <?php echo h($_POST['email']) ; ?>
  <br>
  ホームページ
  <?php echo h($_POST['url']) ; ?>
  <br>
  性別
  <?php if($_POST['gender'] === '0' ){echo '男性';} 
        if($_POST['gender'] === '1' ){echo '女性';} 
  ?>
  <br>
  年齢
  <?php
    if($_POST['age'] === '1'){echo '〜19歳';}
    elseif($_POST['age'] === '2'){echo '20歳〜29歳';}
    elseif($_POST['age'] === '3'){echo '30歳〜39歳';}
    elseif($_POST['age'] === '4'){echo '40歳〜49歳';}
    elseif($_POST['age'] === '5'){echo '50歳〜59歳';}
    elseif($_POST['age'] === '6'){echo '60歳〜';}
  ?>
  <br>
  お問い合わせ内容
  <br>
  <?php echo h($_POST['content']) ; ?>

  <input type="submit" name="back" value="戻る">
  <input type="submit" name="btn_submit" value="送信する">
  <!-- GETやPOSTで1回通信をするとデータが消えるのでhiddenで受け渡す。 -->
  <input type="hidden" name="your_name" value="<?php echo h($_POST['your_name']);?>">
  <input type="hidden" name="email" value="<?php echo h($_POST['email']);?>">
  <input type="hidden" name="url" value="<?php echo h($_POST['url']);?>">
  <input type="hidden" name="gender" value="<?php echo h($_POST['gender']);?>">
  <input type="hidden" name="age" value=" <?php echo h($_POST['age']); ?>">
  <input type="hidden" name="content" value="<?php echo h($_POST['content']);?>">
  <input type="hidden" name="csrf" value=" <?php echo h($_POST['csrf']) ; ?>">
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

<?php if(!empty($_POST['btn_confirm']) && !empty($error)) :?>
<ul>
  <?php foreach($error as $value) :?>
  <li><?php echo $value; ?></li>
  <?php endforeach ;?>
</ul>
<?php endif ;?>
<div class="container">
<div class="row">
  <div class="col-md-6">
    <form method="POST" action="input.php">
    <div class="form-group">
      <labeL for="your_name">氏名</labeL>
      <input type="text" class="form-control" id="your_name" name="your_name" value="<?php echo h($_POST['your_name']) ; ?>" required>
    </div>

    <div class="form-group">
      <labeL for="e-mail">メールアドレス</labeL>
      <input type="text" name="email" value="<?php echo h($_POST['email']) ; ?>">
    </div>

    <div class="form-group">
      <labeL for="url">ホームページ</labeL>
    <input type="text" name="url" value="<?php echo h($_POST['url']) ; ?>">
    </div>
    
    <div class="form-check form-check-inline">性別
      <input class="form-check-input" id="gender1" type="radio" name="gender" value="0">
      <labeL class="form-check-input" id="gender1">男性</labeL>
      <input class="form-check-input" id="gender1" type="radio" name="gender" value="1">
      <labeL class="form-check-input" id="gender1">女性</labeL>
    </div>

    <div class="form-group">
      <label for="age">年齢</label>
      <select class="form-control" id="age" name="age">
        <option value="">選択して下さい</option>
        <option value="1">〜19歳</option>
        <option value="2">20歳〜29歳</option>
        <option value="3">30歳〜39歳</option>
        <option value="4">40歳〜49歳</option>
        <option value="5">50歳〜59歳</option>
        <option value="6">60歳〜</option>
      </select>
    </div>


    <div class="form-group">
      <label for="contact">お問い合わせ内容</label>
      <textarea class="form-control" id="contact" row="3" name="contact"><?php echo h($_POST['contact']) ; ?></textarea>
    </div>

    <div class="form-check">
      <input class="form-check-input" type="checkbox" id="caution" name="caution" value="1">
      <label class="form-check-label" for="caution">注意事項に同意する</label>
    </div>

  
    <input class="btn btn-info" type="submit" name="btn_confirm" value="確認する" >
    <input type="hidden" name="csrf" value="<?php echo $token; ?>">
    </form>
    <?php endif; ?>

  </div><!-- .md-6 -->
</div>
</div>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js" integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI" crossorigin="anonymous"></script>
  </body>
</html>
```

> 引用
[Bootstrap](https://getbootstrap.jp/docs/4.5/components/forms/)
