# 問題  
任意の2つの文字列があります。  
大文字と小文字の違いを無視して、  
どちらかの文字がもう一方の文字の最後にある場合はTrueをない場合はFalseを出力するプログラムを作りましょう。  
（つまり、大文字と小文字は区別されません）。  

```
[出力例]
end_other('Hiabc', 'abc') → True
end_other('AbC', 'HiaBc') → True
end_other('abc', 'abXabc') → True
```

```
[回答例]
def end_other(a,b)
  a_down = a.downcase
  b_down = b.downcase
  a_len = a_down.length
  b_len = b_down.length
  if  b_down.slice!(-(a_len)..b_len - 1) == a_down || a_down.slice!(-(b_len)..a_len - 1) == b_down
    puts "True"
  else
    puts "False"
  end
end
xyz_there('abcxyz')
xyz_there('abc.xyz')
xyz_there('xyz.abc')
>出力結果
True
True
True
```
```
def end_other(a,b)

 a_count = a.length
 b_count = b.length

  if a_count <= b_count
    check = b[-(a_count),b_count]
    p check.casecmp?(a)
  else
    check = a[-(b_count),b_count]
    p check.casecmp?(b)
  end
end

end_other('abcaaaa', 'abXabc')
xyz_there('abcxyz')
xyz_there('abc.xyz')
xyz_there('xyz.abc')
>出力結果
True
True
True
```






> 参考  
[るりまサーチ:Ruby API](https://docs.ruby-lang.org/ja/search/)  
[<DAY148> ドリルより](https://www.yujiro.site/entry/2019/07/19/175209)  

