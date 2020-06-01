# フォームで入力した値をDBに保存  
```
[db_connection.php]
<?php

const DB_HOST = 'mysql:dbname=udemy_php;host=localhost;charset=utf8';
// const DB_USER = 'root';
// const DB_PASSWORD = 'root';
const DB_USER = 'php_user';
const DB_PASSWORD = 'password123';

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

