# CSSの読み込みについて  
* 通常ウェブサイトを作成する際htmlファイルにlinkタグを記述してcssファイルを読む。<br>しかし、Railsではこの記述はいらない。  
【理由】  
* application.html.erbにstylesheet_link_tag 'application'という記述があるため、<br>app/assets/stylesheets/application.cssが読み込まれる。
* application.cssにあるrequire tree .　という記述により、同じフォルダにあるcssファイル全てが読み込まれる。

> 参考
[【Rails入門】スタイルシート（CSS）を使ってWebアプリを装飾しよう](https://www.sejuku.net/blog/64731)
