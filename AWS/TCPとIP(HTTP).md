# HTTP(HyperText Transfer Protocol)  
* インターネットで**HTMLなどのコンテンツの送受信に用いられる通信の約束事**。  
* クライアントが**HTTPリクエスト**を送り、それに対してサーバーが**HTTPレスポンス**を返す。<br>そのリクエスト・レスポンスの書き方がHTTPの正体。  

||HTTPリクエスト<br>「http://aws-and-infra.workのページ見せて」||
|:--:|:----|:--:|
|クライアント|⇆|サーバー|
||HTTPレスポンス<br>「http://aws-and-infra.workのファイル送るよ」|

## HTTPリクエストの中身  
* リクエストライン、ヘッダー(クライアントから送信する追加情報)、ボディから構成される。  

|内容|詳細|
|:--:|:--|
|リクエストライン|GET /HTTP/1.1|
|ヘッダー|Host:example.com<br>User-Agent:Mozilla/5.0<br>Accept-Encoding: gzip, deflate<br>Connection:keep-alive|
|ボディ|特になし（オプション)|

## HTTPレスポンスの中身  
* ステータスライン、ヘッダー(クライアントから送信する追加情報)、ボディから構成される。  

|内容|詳細|
|:--:|:--|
|ステータスライン|HTTP/1.1 200OK|
|ヘッダー|Date:Fri,28 Jun 2019 01:09:23 GMT<br>Content-Type:text/html; charset=UTF-8<br>Cahe-Control: max-age=604800<br>Last-Modified:Fri,09 Aug 2013 23:54:35GMT|
|ボディ|<!doctype html><br> <html> <br>…<br></html>|




