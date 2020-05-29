# PHP設定ファイル(php.ini)  
## エラー関連
* エラーのレベル<br>error_reporting =   
* 全てのエラーを表示<br>E_ALL     
* 軽微なエラーを除いたエラーを表示<br>E_NOTICE      
* ブラウザ上にエラーを表示 On/Off<br>display_errors = On  
* エラーログを吐く設定<br>log_errors = On  
* error_logの設定<br>error_log = /var/log/php.logなど  
## タイムゾーン  
* datr.timezone = "Asia/Tokyo"  

## マルチバイト関連  
* default_charset = "UTF-8"  
* mbstring.language = Japanese  
* mbstring.internal_encoding = UTF-8  
* mbstring.enconding_transtration = Off  
* mbstring.http_input = pass  
* mbstring.http_output = UTF-8    
* mbstring.detect_order = auto 

## セッション  
* session.name = セッション名  
* セッション自動開始 1は有効 0は無効  
session.autostart = 1  




