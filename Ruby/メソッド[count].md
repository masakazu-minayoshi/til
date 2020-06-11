# countメソッド  
## 機能  
①文字列の特定の文字の出現回数を数えるための機能。<br>（例）(「こんばんは」という文字に「ん」は2回みたいに数える機能)
②配列の要素の数を数えるための機能。  
しかし、countだと複数文字をカウントできない。つまり単体しか抽出できない。  
③例
```
word = 'nyyyynnyyy'
puts word.count('')
# => 7
```
```
word = 'rubyrubyrubyrubyrubyrubyruby'
puts word.count('r')
# => 7
```
```
word = 'rubyrubyrubyrubyrubyrubyruby'
puts word.count('ruby')
# => 28
# =>「r,u,b,y」 のどれかにマッチする文字の個数をカウントしてしまう。
```
# scanメソッド  
一致する文字列を抽出して配列にする。  
```
word = 'rubyrubyruby'
puts word.scan('ruby')
# => 
ruby
ruby
ruby

puts word.scan('ruby').length
# => 3
```



> 引用  
[Ruby 2.7.0 リファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/method/Enumerable/i/count.html)  
[Rubyでcountメソッドを使う方法を現役エンジニアが解説【初心者向け】](https://techacademy.jp/magazine/28265)  
[countメソッドの様々な使い方(Ruby)](https://qiita.com/mary_new_programmer/items/dac0c1d5577bc6429380)  
[length、size、count メソッドの違いまとめ【Ruby】](https://qiita.com/motoki4917/items/ffc89d955e20b91d1014)  
