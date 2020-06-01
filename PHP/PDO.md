# PDOでデータベースと接続  
* 接続に成功すると「接続成功」、失敗すると「接続失敗」と表示させる。  
```
[db_connection.php]
<?php
const DB_HOST = 'mysql:dbname=***;host=localhost;charset=utf8';
// const DB_USER = '***';
// const DB_PASSWORD = '***';

//例外処理(exception)
try{
  //データベースへの接続を表す PDO インスタンスを生成する
  //オプションをつける際は配列にして記入する。
  $pdo = new PDO(DB_HOST,DB_USER,DB_PASSWORD,[
    //連想配列としてデータベースの情報を引っ張ってくる
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
    //例外を表示する
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    //SQLインジェクション対策（セキュリティ対策）
    PDO::ATTR_EMULATE_PREPARES => false,
  ]);
    echo '接続成功';
} catch(PDOException $e){
  echo '接続失敗' . $e->getMessage() . "\n";
  exit();
}
?>
```
# PDO プリペアードステートメント プレースホルダ
* phpMyAdminに登録しているデータを引っ張ってくる。  
```
[ユーザー入力なし queryで記載する場合]
<?php
require 'db_connection.php';


//sql文を書く
$sql = 'select * from contacts where id = 4';
//sql文実行し$stmt（ステートメント）に代入。
$stmt = $pdo->query($sql);
//$stmt->fetchall();で取得し$resultに代入。
$result = $stmt->fetchall();
echo '<pre>';
//var_dump($result);で出力。
var_dump($result);
echo '</pre>';
?>
```
```
[ユーザー入力あり prepare, bind, execute]
(why)
悪意のあるユーザーにdeleteされないために
SQLインジェクション対策（セキュリティ対策）する
<?php
require 'db_connection.php';

//sql文を書く
//「:id」つきプレースホルダー
$sql = 'select * from contacts where id = :id';
//sql文実行し$stmt（ステートメント）に代入。プリペアードステートメント。
$stmt = $pdo->prepare($sql);
//実際に紐付けるidが4のinteger型を指定
$stmt->bindValue('id', 3, PDO::PARAM_INT);
//実行
$stmt->execute();

$result = $stmt->fetchall();
echo '<pre>';
//var_dump($result);で出力。
var_dump($result);
echo '</pre>';
?>
```
# PDOトランザクション  
* トランザクション:まとまって処理する時に使う。<br>（例）銀行で残高確認。Aさんが引き落とし->Bさんに振込  
```
<?php

require 'db_connection.php';

//ユーザー入力なし query
$sql = 'select * from contacts where id = :id';

$result = $stmt->fetchall();
echo '<pre>';
//var_dump($result);で出力。
var_dump($result);
echo '</pre>';

$pdo->beginTransaction();
  try{
  //sql処理
  $stmt = $pdo->prepare($sql);
  $stmt->bindValue('id', 3, PDO::PARAM_INT);
  $stmt->execute();
  $pdo->commit();

  }catch(PDException $e){
    //更新のキャンセル
    $pdo->rollback();
}
?>
```



> 引用  
[PHPドキュメント:PDO](https://www.php.net/manual/ja/class.pdo.php)  
[嵐のコンサートがあるとダブルブッキングしてしまうホテル予約システムを作ってみた](https://blog.tokumaru.org/2015/05/blog-post.html)





