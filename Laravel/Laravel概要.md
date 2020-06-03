# Laravelの概要  
## MVCモデル  
* Model・・データベースとやりとり  
* View・・見た目  
* Controller・・処理  
* Routing・・アクセスの振り分け   
* Migration・・DBテーブルの履歴管理  
## Laravel大まかな図  
[![Image from Gyazo](https://i.gyazo.com/2125c273c4166b750c81ea4e076cc02b.png)](https://gyazo.com/2125c273c4166b750c81ea4e076cc02b)
> 引用
[Laravelの構造と処理の流れを【MVCモデル】で初心者向けに解説【model,view,controller】](https://hikopro.com/laravel-mvc/)
## ルーティング (Routing)
```
[routes/web.php]
<?php
//アドレスにアクセスしたらreturnの処理をする関数定義
Route::get('/', function () {
    //viewファイルを表示させなさい
    return view('welcome');
});
```
## ビュー (View) 見た目  
* resources/views/ xxx.blade.php  
* **blade.php とつけるのはお約束**  
## Artisan (職人)  
* ターミナルで「php artisan・・・」と打つと様々な機能を使うことができる。  
* php artisan listとコマンドを打つとartisanが持つリストを表示される。  
## モデル (Model) DBとやりとり  
DBとのやりとりをPHPで書ける。  
* Eloquent(エロクアント)  
* ORM/ORマッパー   
* Object-Relational Mapping  
* オブジェクト関係マッピング  
### モデルファイルの作り方  
ターミナルでコマンド実行。  
* appの直下にモデルを作成。  
%php artisan make:model Test  
* appフォルダの直下にモデルフォルダを作成しモデルを作成。 
%php artisan make:model Models/Test  
* マイグレーションファイルとモデルを同時に作成する。  
%php artisan make:model Models/Test -mc  
## マイグレーション (Migration)  
* 役割：DBテーブルの履歴管理  
※**モデルは単数形 マイグレーションは複数形**  
* マイグレーションファイル生成の手順  
①マイグレーション生成のコマンド  
%php artisan make:migration create_tests_table  
②マイグレーションファイル記入後にマイグレートするコマンド  
%php artisan migrate  
③phpMyAdminで作成されたファイルを確認する。  

> 参考  
[Laravel 6.x データベース：マイグレーション](https://readouble.com/laravel/6.x/ja/migrations.html)

## tinker (DB簡易接続)  
* ターミナルで%php artisan tinker とコマンドを打つと対話型のコマンドシェルが立ち上がる。  
[![Image from Gyazo](https://i.gyazo.com/e618f256b3d9998eb1fc07132e369c31.png)](https://gyazo.com/e618f256b3d9998eb1fc07132e369c31)
* phpMyAdminを確認するとコマンドシェルで記入した内容がデータベースに反映されている。  
[![Image from Gyazo](https://i.gyazo.com/0b4a67a29ce101cfe3344cd831f53aa0.png)](https://gyazo.com/0b4a67a29ce101cfe3344cd831f53aa0)

## コントローラー (処理)  
* php artisanコマンドで作成することができる。<br>（例）php artisan make:controller TestController  
* app/Http/Controllers/ にファイルが作成される。  

## MVCモデルの記述の流れ  
### viewファイルに記載した内容を表示させる場合。   
①[routes/web.php]に遷移先と処理を記載。  
```
<?php
//'tests/test'に遷移したらTestControllerに飛ばしてね
Route::get('tests/test', 'TestController@index');
```
②[app/Http/Controllers/TestController.php]に処理を記載。
```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class TestController extends Controller
{
    //
    public function index()
    {
        //'tests/test'のviewファイルを表示させる。
        return view('tests/test');
    }
}
```
③[resources/views/tests/test.blade.php]にviewに表示させる内容を記載。
```
test
```
④ターミナルで%php artisan serveコマンド実行。  
⑤http://127.0.0.1:8000/tests/testに遷移するとtestと表示されている。  
### DBに登録した内容を表示させる場合。  
（参考）
```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
//Testモデルに登録したデータを引っ張って来る処理
use App\Models\Test;

class TestController extends Controller
{
    //
    public function index()
    {
        //引っ張ってくるデータを変数に代入する。
        $values = Test::all();
        //die + var_dumpをセットにしたコマンド
        //変数の処理を止めて中身を表示させるコマンド
        dd($values);
        //'tests/test'のviewファイルを表示させる。
        return view('tests/test');
    }
}
```
配列でDBに登録されたデータを引っ張ってくる。
[![Image from Gyazo](https://i.gyazo.com/0c0f73390a21cd64c90b0238fbfe11a5.png)](https://gyazo.com/0c0f73390a21cd64c90b0238fbfe11a5)
①[app/Http/Controllers/TestController.php]に処理を記載。
```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
//Testモデルに登録したデータを引っ張って来る処理
use App\Models\Test;

class TestController extends Controller
{
    //
    public function index()
    {
        //引っ張ってくるデータを変数に代入する。
        $values = Test::all();

//'tests/test'のviewファイルにcomact()を使いvaluesのデータを表示させる。
        return view('tests/test', compact('values'));
    }
}
```
②[resources/views/tests/test.blade.php]にviewに表示させる内容を記載。
```
test

@foreach($values as $value)
{{$value->id}}<br>
{{$value->text}}<br>
@endforeach
```
③ブラウザ上に以下のように表示される。  
[![Image from Gyazo](https://i.gyazo.com/2be41f1f433d9187f401ce72b12d743b.png)](https://gyazo.com/2be41f1f433d9187f401ce72b12d743b)


