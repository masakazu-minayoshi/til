# artisanコマンド  
* app/Http/Controllersの中にSampleContorllerというファイルが生成される。
```
php artisan make:controller SampleController
```
# Migrationファイルの作成  
* make:model 〇〇 -m とすることでModelとMigrationを同時に作成してくれる。  

```
[Tweetsテーブル]
php artisan make:model Models/Tweet -m

[Commentsテーブル]
php artisan make:model Models/Comment -m

[Favoritesテーブル]
php artisan make:model Models/Favorite -m

[Followersテーブル]
php artisan make:model Models/Follower -m

```
