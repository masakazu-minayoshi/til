# 問題  
3つの整数a b cが与えられた場合、  
bまたはcがaとの差が１でかつbとｃとの数値の差が2以上の場合はTrue。  
それ以外はFalseと出力するメソッドを作りましょう。  
```
[出力例]
close_far(1, 2, 10) → True
close_far(1, 2, 3) → False
close_far(4, 1, 3) → True

[ヒント]
返り値を整数に変換する際はabsメソッドを使いましょう。

[abs]
対象となる数値に対して「abs」メソッドを実行すると絶対値を取得することができます。  
すなわち正の数の場合はそのままですが負の数の場合は符号を取って正の数にした数値が取得できます。
```
```
num = (-5).abs
```

```
[回答]
def close_far(a, b, c)
  if((b - a).abs == 1 || (c - a).abs == 1) && (b - c).abs >= 2
    puts "True"
  else
    puts "Flase"
  end
end
close_far(1, 2, 10) #True
close_far(1, 2, 3)  #False
close_far(4, 1, 3)  #True

```

> 参考  
[プログラミングな日常](https://cloraordinary.com/rubydorill70)  
