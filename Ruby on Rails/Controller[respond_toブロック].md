# respond_toブロック  
## respond_toブロックとは？  
* controller内で処理した結果を基本的にはHTML形式で返却したいが特定の呼び出しに対しては、<br>明示的にHTML以外の形式で返却したい場合に使用するメソッド
* 送られてきたリクエストによって、レスポンスするフォーマットを振り分けている。
* respond_to |format|　～　end　内では format.XXXXという形で返却形式を設定できる。<br>（HTMLで返却したい場合はformat.htmlという形になる。）

## respond_toの書き方  

```
def index
  respond_to do |format|
    format.html
    format.json {render :json => オブジェクト}
    format.xml  {render :xml => オブジェクト}
  end
end
```

## 問題  
tweetsコントローラ内で、showアクションが定義されています。  
5行目から9行目までの、respond_toブロックは、どのような処理を行なっているか説明しなさい。  
[回答]  
送られてきたリクエストによって、レスポンスを振り分けている。  
例えば、/tweets.jsonというURLでページを開いた場合、json形式で変数@tweetsの中身が展開されます。  

[(tweets.html)](https://tech-master.s3.amazonaws.com/uploads/curriculums//c8cfab80f490a071c4ac3e540bddf2f1.png)
[(tweets.json)](https://tech-master.s3.amazonaws.com/uploads/curriculums//f9ee07c0a47b03ccb3034812181de7b9.png)




```
tweets_controller.rb
def index
  @tweets = Tweet.all

  respond_to do |format|
    format.html # index.html.erb
    format.json { render json: @tweets }
    format.xml  { render xml:  @tweets }
    format.yaml { render text: @tweets.to_yaml }
  end
end
```


> 参考  
[Railsのrespond_toの使い方を現役エンジニアが解説【初心者向け】](https://techacademy.jp/magazine/24827)  
[JSON/XML形式で出力する](https://www.javadrive.jp/rails/controller/index7.html)  
