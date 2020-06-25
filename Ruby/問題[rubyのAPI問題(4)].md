# 問題  
任意の文字列の最初の2文字を最後尾に持ってきてその文字を出力するメソッドを作りましょう。  
```
[参考URL] https://docs.ruby-lang.org/ja/search/
[出力例] 
left2('Hello') → 'lloHe'
left2('java') → 'vaja'
left2('Hi') → 'Hi'
```
```
[回答]
def left2(str)
  puts str[2..-1] + str[0, 2]
end

str = gets.chomp
left2(str)
```

> 参考  
[instance method String#slice!](https://docs.ruby-lang.org/ja/2.6.0/method/String/i/slice=21.html)  
