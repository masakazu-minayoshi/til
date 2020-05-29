# form(入力,確認,完了)  
* formのページを作成する際に下記のやり方がある。  
①入力(input.php)、確認(confirm.php)、完了(thanks.php)の3つのページを作る。  
②入力(input.php)で完結させる。  
（例）②の内容でコードを書いた場合  
```
<?php
echo'<pre>';
var_dump($_POST);
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
  <form method="POST" action="input.php">
  名前
  <?php echo $_POST['your_name'] ; ?>
  <br>
  メールアドレス
  <?php echo $_POST['email'] ; ?>
  <input type="submit" name="back" value="戻る">
  <input type="submit" name="btn_submit" value="送信する">
    <!-- GETやPOSTで1回通信をするとデータが消えるのでhiddenで受け渡す。 -->
    <input type="hidden" name="your_name" value=" <?php echo $_POST['your_name'] ; ?>">
  <input type="hidden" name="email" value=" <?php echo $_POST['email'] ; ?>">
  </form>
  <?php endif; ?>

  <?php if($pageFlag === 2) : ?>
    送信が完了しました
  <?php endif; ?>

  <?php if($pageFlag === 0) : ?>
  <form method="POST" action="input.php">
  名前
  <input type="text" name="your_name" value="<?php echo $_POST['your_name'] ; ?>">
  <br>
  メールアドレス
  <input type="email" name="email" value="<?php echo $_POST['email'] ; ?>">
  <input type="submit" name="btn_confirm" value="確認する">
  </form>
  <?php endif; ?>
</body>
</html>
```




