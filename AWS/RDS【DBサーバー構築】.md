# RDS【DBサーバー構築】  
## RDSって何？  
* RDS:フルマネージドなリレーショナルデータベースのサービス。<br>コア機能の開発に注力できるように設計されている。  
①構築の手間の軽減。  
②運用の手間の軽減。  
③AWSエンジニアによるデータベース設計のベストプラクティスを適用。  
→上記3つのおかげでコア機能の開発に注力できる。（アプリ最適化だけやればOK）

|オンプレミス|On EC2|RDS|
|:-------:|:----:|:--:|
|アプリ最適化|アプリ最適化|アプリ最適化|
|スケーリング|スケーリング|**スケーリング**|
|バックアップ|バックアップ|**バックアップ**|
|アップデート|アップデート|**アップデート**
|OSインストール|**OSインストール**|**OSインストール**|
|物理サーバーの設置|**物理サーバーの設置**|**物理サーバーの設置**|

## RDSの概要  
* 利用可能なエンジン  
・My SQL  
・PstgreSQL    
・Oracke    
・Microsoft SQL Server    
・Amazon Aurora    
・MariaDB    
* 各種設定グループ    
・DBパラメータグループ：DB設定値を制御。    
・DBオプショングループ：RDSへの機能追加を制御。  
・DBサブネットグループ：RDSを起動させるサブネットを制御。  

## RDSの特徴  
* 可用性（障害があっても止まらない）の向上  
・マルチAZを簡単に構築。  
* パフォーマンスの向上  
・リードレプリカを簡単に構築することができる。  
* 運用負荷の軽減  
・自動的なバックアップ  
-1日1回バックアップを自動取得（スナップショット）  
-スナップショットを基にDBインスタンスを作成（リストア）  
・自動的なソフトウェアメンテナンス   
-メンテナンスウィンドウで指定した曜日、時間帯にアップデートを自動実施。  
・監視  
-各種メトリクスを60秒間隔で取得、確認ができる。  

## プライベートサブネットを作成する  
サービスでVCPを選択→VPCダッシュボード内のサブネットを選択→サブネットの作成へ遷移。  

## RDSを設置する  
①EC2ダッシュボード→セキュリティグループを選択→セキュリティグループの作成を選択
②RDSダッシュボード→サブネットグループを選択→DB サブネットグループを作成を選択。<br>アベイラビリティーゾーンは２つ必要なことに注意。  
③RDSダッシュボード→パラメータグループを選択→DB パラメータグループを作成を選択し必要事項記入。  
※編集はチェックボックスにチェックして、パラメータグループアクションの編集を選択→変更可能状態がtrueなら編集できる。  
④RDSダッシュボード→オプショングループを選択しグループの作成をクリック→必要事項を記入。  
※default設定のモノも作成されるが使用するのは自分で作成したモノを使う。  
⑤RDSダッシュボード→データベースを選択しデータベースの作成をクリック→必要事項を記入。  

## WebサーバーからRDSに接続しよう。  
①EC2でインスタンスを選択→IPv4 パブリック IPコピー→

# RDS【DBレイヤを冗長化する】  
## RDSでマスタースレーブ構成にする  
* RDSではマルチAZの機能を使えばマスタースレーブ構成を構築できる。  


> 参考
[RDSのサブネットグループが作成できない。](https://www.wantanblog.com/entry/2019/09/24/225020)


