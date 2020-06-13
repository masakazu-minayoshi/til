# 問題  
以下の条件を満たすコードを記述してください。  
・Bookクラスを作成する。  
・Bookクラスは@titleと@priceをプロパティとして持っている。  
・attr_readerを使用する。  
・Bookクラスのインスタンスを作成する（タイトル、価格は任意）。  
・作成したインスタンスから、タイトルを取得し画面に表示させる。  

```
class Book
  def initialize(title, price)
    @title = title
    @price = price
  end
  def title
    @title
  end
  def price
    @price
  end
end
book = Book.new("走れメロス", "500円")
#インスタンスメソッド実行
puts "タイトル: #{book.title}"
puts "本文: #{book.price}"
```
*  attr_reader:インスタンス変数 name の読み取りメソッドを定義

> 参考  
[Ruby 2.7.0 リファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/method/Module/i/attr_reader.html)  
[【Ruby】attr_accessor、attr_reader、attr_writerの違いを例から理解する](https://qiita.com/chimeiwang/items/7ad47237050d371d760c)  
