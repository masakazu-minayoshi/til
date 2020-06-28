# 問題  
正の整数を入力します。その整数が、10の倍数（10,20,30...）からの差が2以内であるときはTrue<br>それ以外はFalseと出力するメソッドを作りましょう。

```
[出力例]
near_ten(12)→True
near_ten(17)→False
near_ten(19)→True
```
```
def near_ten(num)
  quotient = num % 10
  if quotient <= 2 || quotient >= 8
    puts "Ture"
  else
    puts "Flase"
  end
end

num = gets.to_i
near_ten(num)
>入力:8
>出力:Ture
```

> 参考  
[<DAY133>学習忘備録　ドリルより](https://www.yujiro.site/entry/2019/07/04/215607)  
[[Ruby]dorill67](https://cloraordinary.com/rubydorill67)    
[るりまサーチ:Ruby API](https://docs.ruby-lang.org/ja/search/)  
