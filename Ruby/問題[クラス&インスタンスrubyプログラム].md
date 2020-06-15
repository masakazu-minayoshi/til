# 問題①  
ユーザーに数字を入力してもらい、その数の回数だけHello!と表示させるコードを記述しなさい。  
```
def output(num)
  num.times{ puts "Hello!" }
end

puts "何回表示させますか？"
num = gets.to_i
output(num)
```
> 参考
[【Ruby】Ruby入門：繰り返し処理](https://qiita.com/Mocacamo/items/8c8d2cdab3e2210971e0)  


# 問題②  
以下の仕様にしたがってコードを記述してください。  
・Personクラスはプロパティ name, ageを持っている。  
・StudentクラスはPersonクラスを継承している。  
・Studentクラスにはintroduceメソッドが定義されている。実行すると  
　「私の名前は◯◯です。◯歳です」と表示がされる。  
・Studentクラスのインスタンスを作成し、introduceメソッドを実行する。  

```
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end
end

class Student < Person
  def introduce
    puts "私の名前は#{@name}です。#{@age}です"
  end
end

yamada = Sutdent.new("山田", 20)
yamada.introduce
```

> 参考
[クラスのメソッドをオーバーライドするには？](https://www.buildinsider.net/language/rubytips/0014)
