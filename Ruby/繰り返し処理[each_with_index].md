# [問題]配列を利用したrubyプログラムの作成  
以下の配列から、数を探して何番目に含まれているか結果を返すメソッドを作成してください。  

```
input = [3, 5, 9 ,12, 15, 21, 29, 35, 42, 51, 62, 78, 81, 87, 92, 93]
（使用例）
search(12, input)
=> 4番目にあります
search(7, input)
=> その数は含まれていません

[コード]
def search(target_num, input)
  input.each_with_index do |num, index|
    if num == target_num
      puts "#{ index + 1}番目にあります"
      return
    end
  end
  puts "その数は含まれていません"
end
input = [3, 5, 9 ,12, 15, 21, 29, 35, 42, 51, 62, 78, 81, 87, 92, 93]
search(11, input)
```


> 参考  
[【Ruby】繰り返し処理にインデックスをつける(each_with_index, with_index)](https://qiita.com/tomokichi_ruby/items/46094a5fecbd46906f93)  
[Ruby 2.7.0 リファレンスマニュアル ](https://docs.ruby-lang.org/ja/latest/method/Enumerable/i/each_with_index.html)  
[each_with_indexをうまく使う【rubyアルゴリズム】](https://www.y-hakopro.com/entry/2019/08/29/230524)
