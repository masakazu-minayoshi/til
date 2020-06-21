# CSRF(クロスサイトリクエストフォージェリ)      
## CSRF(クロスサイトリクエストフォージェリ)とは？  
* Webアプリケーションの脆弱性を利用したサイバー攻撃の一種。  
* ユーザーによる認証が完了したと考えられるWebアプリケーションのページに、悪意のあるコードやリンクを仕込むというもの。  

## クラッキング  
コンピュータネットワークに繋がれたシステムへ不正に侵入したり、<br>コンピュータシステムを破壊・改竄するなど、コンピュータを不正に利用すること。

## Railsでの対策方法  
```
[ApplicationControllerにデフォルトで下記記述がされている]
protect_from_forgery with: :exception
```
* アプリで作られたフォームに対してトークンが発行され、<br>正しいフォームからの通信なのかを判別することができる。  


> 参照  
[Rails セキュリティガイド](https://railsguides.jp/security.html#%E3%82%AF%E3%83%AD%E3%82%B9%E3%82%B5%E3%82%A4%E3%83%88%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%83%95%E3%82%A9%E3%83%BC%E3%82%B8%E3%82%A7%E3%83%AA-csrf)  
[クラッキングとは？具体的手口やハッキングとの違い、対策について徹底解説](https://cybersecurity-jp.com/cyber-terrorism/24253)  
[CSRFに対するRailsのセキュリティ対策について](https://qiita.com/okamoto_ryo/items/990e26462427adcadf22)  
