# 問題  
任意の文字に対してn番目の文字を消し、その消した文字を出力するメソッドを作りなさい。  
※ヒント：APIを利用して問題を解きましょう。  
[参考URL]<br>https://docs.ruby-lang.org/ja/search/  

[呼び出し方]<br>missing_char(string, num)  

[出力例]
```
missing_char('kitten', 1) → 'itten'
missing_char('kitten', 2) → 'ktten'
missing_char('kitten', 4) → 'kittn'
```

[回答]
```
def missing_char(array, n)
  array.slice!(n)
  puts array
end
```


> 参考  
[任意の文字列の最初の2文字を最後尾に持ってきて その文字を出力するメソッド](https://qiita.com/okamoto_ryo/items/d215dd5349ad52f87cd3)  
[sliceメソッド](https://www.javadrive.jp/javascript/array_class/index8.html)  




