# attr_accessorメソッド  
* attr_accessorメソッド:ゲッター、セッターを簡単に定義できるメソッド。   
* インスタンス変数が多い時に、全てのゲッターを地道に定義し行数が多くなることを防ぐことができる。  
* (ex1)と(ex2)それぞれの定義は同様に評価される。  
```
(ex1)
class Dog
  attr_accessor :name, :type, :age
end
```
```
(ex2)
class Dog

  def name
    @name
  end

  def name=(name)
    @name = name
  end

  def type
    @type
  end

  def type=(type)
    @type = type
  end

  def age
    @age
  end

  def age=(age)
    @age = age
  end

end
```
