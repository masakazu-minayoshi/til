# 問題  
任意の文字列が "xyz"を含み、xyzの前にピリオド（.）が続かない場合はTrueを出力します。  
したがって、 "xxyz"はカウントされますが、 "x.xyz"はカウントされないメソッドを作りましょう。  

```
[出力例]
xyz_there('abcxyz') → True
xyz_there('abc.xyz') → False
xyz_there('xyz.abc') → True
```

```
[回答例]
def xyz_there(str)
  if str.include?(".xyz") 
    puts "Flase"
  elsif str.include?("xyz")
    puts "True"
  else
    puts "Flase"
  end
end
xyz_there('abcxyz')
xyz_there('abc.xyz')
xyz_there('xyz.abc')
>出力結果
True
Flase
True
```


> 参考  
[るりまサーチ:Ruby API](https://docs.ruby-lang.org/ja/search/)  
