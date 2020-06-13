# 問題  
配列の内部に、複数のユーザーの情報をハッシュとして持つ変数user_dataがあります。  
user_dataを利用して、全てのユーザーの名前だけが出力されるようにRubyでコーディングしてください。  
ただし、出力結果は次のようになるものとします。  

```
[出力結果]
George
Alice
Taro
```


 ```
user_data = [
  {
    user: {
        profile: {
            name: 'George'
        }
    }
  },
  {
    user: {
        profile: {
          name: 'Alice'
        }
    }
  },
  {
    user: {
        profile: {
            name: 'Taro'
        }
    }
  }
]

[回答例]
#puts 変数名[:key1][:key2][:key3]と各キーを取り出す
user_data.each do |u|
  puts u[:user][:profile][:name]
end

あるいは

user_data.each{ |u| puts u.dig(:user, :profile, :name) }

```

> 参考
[Rubyハッシュからの取り出し](https://qiita.com/TANIOKA_Akihiro/items/dcf3a3fa69c34ea91102)  
