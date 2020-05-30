# バリデーション  
```
[validation.php]
<?php

function validation($data) {
  //処理の条件を定義
  //ローカル変数だから外側から使うことができない。
  // →だからinputで$errorを定義する
  $error = [];
  //処理を実行する際の条件定義「名前が未記入だったら実行」
  if(empty($data['your_name']) || 20 < mb_strlen($data['your_name'])) {
    //氏名のバリデーション
    $error[] = '氏名は20文字以内で入力して下さい。';
  }

  //メールアドレス(空かメールアドレスの形式になっていなかったら)
  if(empty($data['email']) || !filter_var($data['email'], FILTER_VALIDATE_EMAIL)) {
    $error[] = '「メールアドレス」は正しい形式で入力して下さい';
  }
  //url
  if(!empty($data['url'])){
    if(!filter_var($data['url'], FILTER_VALIDATE_URL)){
      $error[] = '「ホームページ」は正しい形式で入力してください。';
    }
  }
  //性別(設定（チェック）がされているかどうかで確認)
  if(!isset($data['gender'])) {
    $error[] = '「性別」は必ず入力して下さい。';
  }
  //年齢（選択が空ではないかを確認。emptyは0も含む。）
  if(empty($data['age']) || 6 < $data['age']) {
    $error[] = '「年齢」は必ず入力して下さい。';
  }
  //お問い合わせ内容
  if(empty($data['contact']) || 200 < mb_strlen($data['contact'])) {
    //氏名のバリデーション
    $error[] = '「お問い合わせ内容」は200文字以内で入力してください。';
  }
  //注意事項
  if($data["caution"] !== "1"){
    $error[] = "「注意事項」をご確認ください。";
  }
return $error;
}

?>
```
```
[input.php]
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

  <form method="POST" action="input.php">
  氏名
  <input type="text" name="your_name" value="<?php echo h($_POST['your_name']) ; ?>">
  <br>
  メールアドレス
  <input type="text" name="email" value="<?php echo h($_POST['email']) ; ?>">
  <br>
  ホームページ
  <input type="text" name="url" value="<?php echo h($_POST['url']) ; ?>">
  <br>
  性別
  <input type="radio" name="gender" value="0">男性
  <input type="radio" name="gender" value="1">女性
  <br>
  年齢
  <select name="age">
    <option value="">選択して下さい</option>
    <option value="1">〜19歳</option>
    <option value="2">20歳〜29歳</option>
    <option value="3">30歳〜39歳</option>
    <option value="4">40歳〜49歳</option>
    <option value="5">50歳〜59歳</option>
    <option value="6">60歳〜</option>
  </select>
  <br>
  お問い合わせ内容
  <textarea name="content" value="<?php echo h($_POST['content']) ; ?>"></textarea>
  <br>
  注意事項のチェック
  <input type="checkbox" name="caution" value="1">注意事項にチェックする
  <br>
  
  <input type="submit" name="btn_confirm" value="確認する">
  <input type="hidden" name="csrf" value="<?php echo $token; ?>">
  </form>
  <?php endif; ?>
</body>
</html>
```
