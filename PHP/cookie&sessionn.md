# cookie&sessionn  
## CSRF対策  
* $_GETと$_POSTは1回の画面遷移のみ。  
* $_SESSIONはページ遷移してもデータが残る。<br>→$_SESSIONを使ったトークンを発行。  
## cookie&sessionnの違い  
||cookie|sessionn|
|:--:|:--:|:--:|
|情報の管理|ブラウザ上|サーバー上|

## コード例＆イメージ
[![Image from Gyazo](https://i.gyazo.com/7a15404cac230cfd14c436c2dad4ca89.png)](https://gyazo.com/7a15404cac230cfd14c436c2dad4ca89)
```
[sessiontest_1.php]
<?php
session_start();
?>
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

<?php
//sessionがなかったら実行する条件を定義
if(!isset($_SESSION['visited'])) {
  echo '初回訪問です';
  //sessionは連想配列なのでkeyとvalueで結びつける。
  $_SESSION['visited'] = 1;
  $_SESSION['date'] = date('c');
} else {

  $visited = $_SESSION['visited'];
  $visited++;
  $_SESSION['visited'] = $visited;

  echo $_SESSION['visited'].'回目の訪問です<br>';
  //sessionがあったら出力する条件を定義
  if(isset($_SESSION['date'])) {
    echo '前回訪問は'.$_SESSION['date'].'です';
    $_SESSION['date'] = date('c');
  }

  //setcookie("id", 'aaa', , '/');

echo '<pre>';
var_dump($_SESSION);
echo '</pre>';

echo '<pre>';
var_dump($_COOKIE);
echo '</pre>';
}
?>
</body>
</html>
```

> 引用  
[PHPドキュメント:クッキー(Cookies)](https://www.php.net/manual/ja/features.cookies.php)  
[PHPドキュメント:セッション処理](https://www.php.net/manual/ja/book.session.php)  

## cookie&sessionnの削除  
[![Image from Gyazo](https://i.gyazo.com/8f49e46286a1e7272d7f4c18779c5d44.png)](https://gyazo.com/8f49e46286a1e7272d7f4c18779c5d44)
```
[sessiontest_2.php]
<?php
session_start();
?>

<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

<?php
echo 'セッション廃棄しました';
//空の配列を変数に代入することで上書きする。
$_SESSION = [];
//cookieにも情報が残っているので空の情報を入れつつ日付を更新。
if(isset($_COOKIE['PHPSESSID'])){
  setcookie('PHPSESSID', '', time() -1800, '/');
}
//sessionを削除する
session_destroy();

echo 'セッション';
echo '<pre>';
var_dump($_SESSION);
echo '</pre>';

echo 'クッキー';
echo '<pre>';
var_dump($_COOKIE);
echo '</pre>';
?>
</body>
</html>
```


> 引用  
[ログイン機能の実装サンプル（PHP／MySQL）](https://tadworks.jp/archives/1147)


