# 問題  
あなたは警官です。aとｂ二人の容疑者の取り調べをしています。  
どちらも証言がTrue、またはFalseであればその証言はTrueです。  
しかしどちらかがFalseでTrueであればその証言はFalse、と出力するメソッドを作りましょう。  
```
[呼び出し方]
police_trouble(a, b)
[出力例]
police_trouble(true, false) → False
police_trouble(false, false) → True
police_trouble(true, true) → True
```

[回答例]
```
def police_trouble(a, b)
  if a && b || !a && !b
    puts "True"
  else
    puts "Flase"
  end
end
```

> 参考  
[Rubyで使われる記号の意味（正規表現の複雑な記号は除く）](https://docs.ruby-lang.org/ja/latest/doc/symref.html)  
[Ruby入門 - 演算子](http://www.tohoho-web.com/ruby/operators.html)  
