# display_errorsとは？  
* 開発環境でエラーを表示させるデバック。  

# display_errorsの設定手順    
① MAMP  
② binフォルダ  
③php  
④使用しているphpのversionのフォルダ  
⑤confフォルダ  
⑥php.iniのファイル内でOffからOnにする。
```
display_errors = Off

⇨ display_errors = On
```
# 備考  
## ①必ずApacheのサーバーを落として変更後は再起動を行う。    
## ②プログラム中で動的に設定することもできる。  
* エラーが発生した場合、出力されるHTMLの先頭にエラー内容が表示される。  
```
<?php
ini_set('display_errors', "On");
?>
```
* 表示をしないようにする時は下記コードを入力。
```
ini_set('display_errors', "Off");
```

引用 >
[PHPのdisplay_errorsでエラーを表示させる方法を現役エンジニアが解説【初心者向け】](https://techacademy.jp/magazine/22843)  
