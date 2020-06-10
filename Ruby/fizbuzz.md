# fizbuzz  
```
i = 1
while i<= 100 do
  if i % 15 == 0
    puts "fizzbuzz"
  elsif i % 5== 0
    puts "buzz"
  elsif i % 3 == 0
    puts "fizz"
  else
    puts i
  end
  i += 1
end
```
## elsifを使わないversion
```
i = 1
while i<= 100 do
  str = ""
  if i % 3 == 0
    str = str + "fizz"
  end
  if i % 5== 0
    str = str + "buzz"
  end
  if str == ""
    str = str + i.to_s
  end
  puts str
  i += 1
end
```
```
num = 1
while num < 101
  str = ""
  if num % 3 == 0
    str = str + "fizz"
  end

  if num % 5 == 0
    str = str + "buzz"
  end
  if str == ""
    str = str + num.to_s
  end
  puts str
  num += 1
end
```
> 参考
[elsifを使わずにfizbuzzを実現【Ruby】](https://www.y-hakopro.com/entry/2019/08/21/210243)
