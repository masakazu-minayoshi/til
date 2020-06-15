# 問題  
FizzBuzzという言葉遊びがあります。  
1から数を数えていく際に、それが3の倍数だったら「Fizz」,5の倍数だったら「Buzz」、15の倍数の時は「FizzBuzz」と言います。  
例） 1, 2, Fizz, 4, Buzz, Fizz ,,,,  
このFizzBuzzを再現できるメソッドを作成してください。ただし、いくつまでカウントするか、引数で指定できるものとします。  

```
def fizzbuzz(max_num)
  (1..max_num).each do |num|
    if num %15 == 0
      puts "FizzBuzz"
    elsif num % 5 == 0
      puts "Buzz"
    elsif num % 3 == 0
      puts "Fizz"
    else
      puts max_num
    end
  end
end

puts 'いくつまで数えますか？'
num = gets.to_i
fizzbuzz(num)
```

> 参考
[FizzBuzzで始めるRuby](http://ore-public.github.io/2013/11/02/fizzbuzzruby/)  
