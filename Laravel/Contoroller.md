# Controller  
## Controllerで処理を集中管理しよう  
```
[web.php]
<?php

use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('welcome');
});
//第2引数はコントローラーのファンクション(@のこと）を呼び出すように指定指定いる。
Route::get('/sum/{x}/{y}/' , 'MathController@sum' );
```
```
[MathController.php]
<?php
namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\View;

class MathController extends Controller {
  public function sum($x,$y) {
    $sum = $x + $y;
    return View::make('sum', ['x'=>$x, 'y'=>$y,'sum'=>$sum]);
  }
}
?>
```
```
[sum.blade.php]
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>足し算</title>
</head>
<body>
  <h1>足し算</h1>
  <p>{{ $x }} + {{ $y }} = {{ $sum }}</p>
</body>
</html>
```

> 引用
[Laravel入門 #04：Controllerで処理を集中管理しよう](https://www.youtube.com/watch?v=tThGPwM1qAI&list=PLh6V6_7fbbo8bb7eajaLdsQZ9fLhMJ-oc&index=4)  

