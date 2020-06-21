# scaffold  
## scaffoldとは？  
* Railsに用意されているジェネレータの1つで「足場」を意味し、<br>最低限のCRUDを自動で生成してくれる便利な機能。  
* コマンド1つで、コントローラー、モデル、ビュー、ルーティングを全て用意してくれる。  
```
[コマンド]
$ rails g scaffold モデル名 カラム名:型
```

## 作成手順の例  
```
以下の仕様を満たすRailsアプリケーションを作成して下さい。  
・authorsテーブルがある。
・booksテーブルがある。
・authorsとbooksは１対多のアソシエーションが組まれている。
・authorsテーブルのレコードを削除すると、関連するbooksテーブルのレコードも同時に削除される。
```
[手順]
```
（ターミナル）
> rails new sample-app -d mysql
> rails g scaffold author name:string
> rails g scaffold book name:string author:references

(author.rb)
class Author < ApplicationRecord
  has_many :books ,dependent: :destroy
end
```

> 参考  
[覚えておくと超便利！Ruby on Railsのscaffoldの使い方【初心者向け】](https://techacademy.jp/magazine/7204)  
[rails g scaffoldとは？](https://qiita.com/s_tatsuki/items/3752a9b5a44a9d0023bd)  
[Rails初心者はscaffoldとresourcesを使うな](https://qiita.com/723ch/items/1829124158bd40f3698f)  

