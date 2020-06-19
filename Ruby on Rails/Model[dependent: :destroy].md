# belongs_toメソッド  
## dependent: :destroy  
* dependent: :destroyを指定したクラスが消えた場合に、<br>dependent: :destroyを設定したモデル（のインスタンス）がdestroyされる。

```
class Article < ActiveRecord::Base
  belongs_to :user, dependent: :destroy 
end
```
* 上記コードの例にすると、belongs_toはメソッドであり、<br>:userが第一引数、dependent: :destroyが第二引数となっている。<br>第二引数の記述はハッシュの{}を省略した形で、{dependent: :destroy }を意味している。  
* dependent: :destroyを指定したクラス：Article、<br>dependent: :destroyを設定したモデル（のインスタンス）：userとなるので、<br>Articleが消えるとUserが消えることになる。







> 参考  
[[Rails] has_manyおよびbelongs_toへのdependent: :destroyの設定について](https://qiita.com/after4649/items/1ad419dc705f807735e0)
