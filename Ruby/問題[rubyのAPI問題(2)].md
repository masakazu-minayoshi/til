# 問題  
配列の中に複数の数字を入れて9だけカウントし  
「配列の中には9が3個です」と出力させるメソッドを作りましょう。  
```
[参考URL] https://docs.ruby-lang.org/ja/search/  
[呼び出し方] array_count9(nums)

[出力例]
array_count9([1, 2, 9]) → 1
array_count9([1, 9, 9]) → 2
array_count9([1, 9, 9, 3, 9]) → 3
```

```
[回答例]
def array_count9(nums)
  count = nums.count(9)
  puts count
end
```
