# 正規表現とvalidation  
## 問題  
2行目のvalidationを完成させてください。  
ただし条件は、「youtube」という文字が投稿された文字列に含まれていることを確かめることとします。
```
class Impression < ActiveRecord::Base
  VALID_YOUTUBE_URL_REGEX = ???
  validates :url, presence: true, format: { with: VALID_YOUTUBE_URL_REGEX }
end
```
[回答]
```
VALID_YOUTUBE_URL_REGEX = /\A.*youtube.*\z/
validates :text, presence: true, format: { with: VALID_YOUTUBE_URL_REGEX }
```
[補足]  
* 「/」正規表現オブジェクトを作成する時に「/パターン/」の形式で作成が可能<br>となるため操作したい文字列をスラッシュで挟む
* 「\A」文字列の先頭  
* 「\z」文字列の末尾  
* 「.」は改行を除く任意の1文字にマッチ。<br>ただし、複数行モードでは改行にもマッチする。  
* 「*」は直前の正規表現の0回以上の反復  



> 参考  
[正規表現validation＿定められた文字が投稿された文字列に含まれる](https://qiita.com/susia9610/items/0842b314a417a8f023ec)  
[直前の文字を0回以上繰り返し(*)](https://www.javadrive.jp/ruby/regex/repeat/index2.html)  
[任意の一文字(.)](https://www.javadrive.jp/ruby/regex/repeat/index1.html)  
[Rubyのバリデーション用正規表現集](https://gist.github.com/nashirox/38323d5b51063ede1d41)  




