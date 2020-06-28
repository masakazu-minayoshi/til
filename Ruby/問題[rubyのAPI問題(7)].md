# 問題  
任意の文字列にcatとdogの文字が2つで１組ならTrueそれ以外だとFalseを出力するメソッドを作りましょう。

```
[出力例]
cat_dog("catdog") → True
cat_dog("catcat") → False
cat_dog("1cat1cadodog") → True
```
```
[回答]
def cat_dog(str)
  if str.include?("cat") && str.include?("dog")
    puts "True"
  else
    puts "Flase"
  end
end
cat_dog("catdog")
cat_dog("catcat")
cat_dog("1cat1cadodog")
>出力結果
True
Flase
True

```

> 参考  
[るりまサーチ:Ruby API](https://docs.ruby-lang.org/ja/search/)  
