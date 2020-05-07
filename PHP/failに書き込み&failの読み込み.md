# ファイルに内容を書き込む時に使う関数(function)    
* **file_put_contents**
（例①） news_dateのフォルダ内のnews.txtファイルに内容を書き込む。  
```   
<?php
$success =file_put_contents('../../news_date/news.txt','2020-05-05 ホームページリニューアルしました');
if ($success) {
  print('ファイルへの書き込みが完了しました。');
} else {
  print('書き込みに失敗しました。フォルダの情報などを確認して下さい');
}
?>
```   
[出力内容](https://gyazo.com/434138b3202565faf1c33081ad6e51a0)  
（例②） 例①で書き込んだ内容の前の行に内容を追加する。  
```
<?php
$news = file_get_contents('../../news_date/news.txt');
$news = "2020-05-04 ニュースを追加しました。\n" .$news;
file_put_contents('../../news_date/news.txt', $news);
print($news);
?>
```  
[出力内容](https://gyazo.com/2d0aeeeb12e32e10c1d2e5858987e0ab)  


## 補足  
①一つ上の階層に移動する時は「../」でと入力すると移動できる。    
②文字を追加する際は比較演算子の様に下記手順で追加ができる。  
```  
// // $s = $s .'add';
// // $s .= 'add';
```  

# ファイルの内容を読み込む時に使う関数(function)   
① **file_get_contents**    
```
<?php
$news = file_get_contents('../../news_date/news.txt');
print($news);
?>
```  
* 戻り値を指定して機能する関数(function)。  
* ファイルの内容を再加工したり受け取った内容を使ってファイルを編集できる。  
② **readfile**  
```
readfile('../../news_date/news.txt');
```  
* 戻り値を指定しなくても機能する関数(function)。  
* ファイルの内容を再加工したり受け取った内容を使ってファイルを編集できない。  
