# 問題  
同じ結果を得るために、以下のコードをワンライナーに書き換えなさい。  
```
[元のコード]
array = [1, 2, 3, 4, 5].map do |el| 
  if el.odd?
    el 
  end
end.compact!

[書き換え]
array = [1, 2, 3, 4, 5].map { |el| el if el.odd? }.compact!
array = (1..5).to_a.delete_if { |el| el.even? }
array = (1..5).to_a.delete_if(&:even?)
array = [1, 2, 3, 4, 5].select{ |el| el.odd?}]
```

> 参考
[配列を順番に処理するメソッドの色んな書き方](https://www.ryotaku.com/entry/2019/01/13/143227)
