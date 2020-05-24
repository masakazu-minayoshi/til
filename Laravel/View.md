# View  
## Viewで表示の処理を分けよう  

```
<?php

use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('welcome');
});

//(第1引数):どういうパスで来た時に、(第2引数)どういうアクションを行うのか？
Route::get('/archives/', function() {
    //階層はスラッシュではなくカンマで繋げる
    return view('archives.index');
});
//{}に変数を入れて使用する
Route::get('/archives/{category}/', function($category) {
 //階層はスラッシュではなくカンマで繋げる。//連想配列
    return view('archives.category', ['category' =>$category]);
});
```
```
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{$category}}の一覧</title>
</head>
<body>
  <p>{{$category}}の一覧</p>
  //変数が'news'ならという条件分岐で文字の表示を選択させる。
  @if ($category == 'news')
    <p>本日のニュースをお伝えします</p>
  @endif
</body>
</html>
```
> 引用
[Laravel入門 #03：Viewで表示の処理を分けよう](https://www.youtube.com/watch?v=SNRU9CiJo8Y&list=PLh6V6_7fbbo8bb7eajaLdsQZ9fLhMJ-oc&index=3)  
