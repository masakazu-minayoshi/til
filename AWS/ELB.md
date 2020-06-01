# ELB
## 稼働率を上げるための基本的な考え方  
* 障害発生間隔を長くする。  
* 平均復旧時間を短くする。  
### そのための手法  
* **冗長化**（システムの構成要素を多重化すること）。    
ある構成要素で障害が発生しても処理を引き継げるようにすることで稼働率を高める。<br>→**単一障害点(SPOF)をなくす**。  
### 稼動率を上げる具体的な方法  
①要素単体の稼働率を高くする。  
②要素を組み合わせて、全体の稼働率を高くする。<br>要素を組み合わせることで、サービス構成を冗長化させる。      
[![Image from Gyazo](https://i.gyazo.com/7001a23ceeaaf04ac824038a5f253b68.png)](https://gyazo.com/7001a23ceeaaf04ac824038a5f253b68)
③負荷を適切なプロビジョニングで回避する。  
アクセス数などを予測し適切にリソースを準備する（プロビジョン）のことで、負荷を捌けるようにする。  

|スケールアップ|スケールダウン|
|:--|:--|
|サーバーなど個々の要素の性能を向上させる|サーバーなど個々の要素の数を増やす|
|ある程度の規模まではスケールアップが<br>コストパフォーマンスがよいが、一定範囲を超えると悪くなる。|ある程度の規模を超えそうであれば、<br>スケールアウトで対応する|
||最低限用意しておくべきがN＋1構成、<br>安心なのはN＋2構成|

## サーバー構成のベストプラクティス
### 基本的な構成  
* 一番最小限の構成は１台のサーバーでWebとDBを運用する。  
* パターン①：Webサーバー×①、DBサーバー×1の構成    
・１台のサーバースペック（現行構成）が足りなくなった時に、DBを別のサーバーに切り出す。  
・DBサーバーはセキュリティの観点で切り分ける。  
* パターン②：Webサーバー×2、DBサーバー×1の構成  
・Web側の性能が足りない時にウェブサーバーを複数台使うことで、<br>Webの冗長化と負荷分散を行う。  
* パターン③Webサーバー×②、DBサーバー×2の構成  
・DBをマスタースレーブ方式にすることでDBの冗長化を行う。<br>→Webの冗長化と負荷分散、DBの冗長化ができている。  
## ELBとは？  
### ロードバランサーとは？
※ロードバランサー：各サーバーにアクセスを振り分け、負荷を分散する装置。  
[![Image from Gyazo](https://i.gyazo.com/e7c9c48c49cc0af49cd738f084f41ff4.png)](https://gyazo.com/e7c9c48c49cc0af49cd738f084f41ff4)
### ELB(Elastic Load Balancing)とは何？  
* ELB：AWS上のロードバランサー  
【概要】  
* 複数のEC2インスタンスに**負荷分散**する。  
* 複数のアベイラビリティーゾーンにある複数のEC2インスタンスの中から、<br>正常なターゲットにのみ振り分ける（**ヘルスチェック**）。  
【特徴】  
* **スケーラブル**：ELB自体も負荷に応じて自動でスケールアウト、スケールインする。  
* **アベイラビリティーゾーンを跨る構成**：<br>ELBを利用する場合一つのリージョンを選び、　<br>そのリージョン内のアベイラビリティーゾーンに跨るように構成できる。  
* **名前解決**：  
・ELBにはDNS名が割り当てられる。  
・**ELBへの接続ポイントへのアクセスにはDNSを使用する**。  
* **安価な従量課金**：従量課金で利用可能。  
* **マネージドサービス**：運用が楽。  





