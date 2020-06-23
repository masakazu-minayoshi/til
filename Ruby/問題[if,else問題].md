# 問題  
```
平日でないまたは休日の場合は「True」と返信し、
休日ではない場合は「False」と条件分岐させるメソッドを作りましょう。

呼び出し方：
sleep_in(weekday, vacation)

出力例：
sleep_in(false, false) → False
sleep_in(true, false) → False
sleep_in(false, true) → True
```
```
[コード]
def sleep_in(weekday, vacation)
  if vacation == false
    puts "False"
  else 
    puts "True"
  end
end

weekday = true
vacation = false
sleep_in(weekday, vacation)
```

> 参考  
[if文練習](https://qiita.com/eve1224/items/d4dd3ba441aba17bbdc2)  
