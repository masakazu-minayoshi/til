# Routesで操るURL  
* （例①)routes/web.phpにルーティングを記載  
```
<?php

use Illuminate\Support\Facades\Route;

/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
|
| Here is where you can register web routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/

Route::get('/', function () {
    return view('welcome');
});

//(第1引数):どういうパスで来た時に、(第2引数)どういうアクションを行うのか？
Route::get('/archives/', function() {
    //関数のアクションを記載。
    return'記事一覧';
});
//{}に変数を入れて使用する
Route::get('/archives/{category}/', function($category) {
    return $category . 'の一覧';
});

//フォームで入力されたら完了ページへ遷移。
Route::post('/join/',function() { 
    return'入会申し込み完了';
});

//直接、/joi/のURLを入力されてもリダイレクトするように設定する。
Route::get('/join/', function () {
    return redirect()->to('/');
});

Route::get('/{id}/', function($id) {
    return $id . 'のページ';
});
```
* (例②) コントローラーを経由して「helloWorld!」と表示させる。<br>http://localhost/laravel_sample/public/test/func<br>へアクセスされた時、TestControllerのfunc関数を実行するというルーティングを設定します。   

```
[routes/web.php]
<?php

use Illuminate\Support\Facades\Route;

Route::get('/test/func','TestController@func');
?>
```
```
[app/Http/Controllers/Controller.php]
<?php
namespace App\Http\Controllers;
use Illuminate\Http\Request;

class TestController extends Controller
{
  public function func(){
    return view('sample');
  }
}
?>
```
```
[resources/views/sample.blade.php]
<html>
  <head>
    <title>HelloWorld</title>
  </head>
  <body>
    <h1>HelloWorld!</h1>
  </body>
</html>
```





