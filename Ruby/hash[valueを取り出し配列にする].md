# 問題  
以下のハッシュから値だけを取り出し、配列にしてください。ただし、hashクラスのvaluesメソッドは利用しない。
attr = {name: "八村塁", age: 22, height: 203, weight: 105}
```
attr = {name: "八村塁", age: 22, height: 203, weight: 105}
#空の配列を生成
values = []
attr.each do |key, value| 
#valueをvaluesに代入させる
  values << value
end
puts values
>>
八村塁
22
203
105
```

> 参考  
[Rubyでハッシュオブジェクトからキーや値を取り出す方法【初心者向け】](https://techacademy.jp/magazine/19786)  
[【Ruby入門】ハッシュ（hash）をeachで取り出す！その他ハッシュの応用について](https://style.potepan.com/articles/5433.html)  
