# 問題  
1,2,3が全て配列内に入っていれば「True」それ以外は「False」と出力されるメソッドを作りましょう。  
```
[参考URL] https://docs.ruby-lang.org/ja/search/
[呼び出し方] array123(nums)

[出力例]
array123([1, 1, 2, 3, 1]) → True
array123([1, 1, 2, 4, 1]) → False
array123([1, 1, 2, 1, 2, 3]) → True
```
```
[回答]
def array123(nums)
  if (nums.include?(1) && nums.include?(2) && nums.include?(3))
    puts "True"
  else
    puts "False"
  end
end
```
> 参考  
[るりまサーチ:Ruby API](https://docs.ruby-lang.org/ja/search/)  
