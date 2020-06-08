```
# 空のハッシュ hashを定義する
hash = {}
# keyとvalueを設定する
hash[:name] = "Suzuki"
hash[:height] = 1.6
hash[:weight] = 60
# BMI(体重(kg) ÷ 身長(m) の二乗)を算出
# roundで切り捨て
hash[:bmi] = (hash[:weight] / hash[:height] ** 2).round(1)
# each文でhashを「key:value」で表示させる。
hash.each do |key, value|
puts "#{key}: #{value}"
end
```
> 参考
[Rubyで数値の切り捨て・切り上げ・四捨五入する](https://uxmilk.jp/43388)
