# AWSのネットワークの概念  
* リージョン：AWSの各サービスが提供されている地域のこと。  
※リージョンによって使えるサービスが異なる。（アメリカが早い）  
* アベイラビリティゾーン：独立したーデータセンター。  
・災害に対応するため世界中にある。  
* VPC(Virtual Private Cloud) :AWSに仮想ネットワークを作成できるサービス。  
* サブネット：VPCを細かく区切ったネットワーク。  
セキュリティーの構成を高めるためにインターネットから接続できる所とできない所それぞれ作成する。  
・パブリックサブネット：インターネットから接続できるサブネット。後々、webサーバを設置する。   
・プライベートサブペット：インターネットから隠すためのサブネット。後々、データベースサーバを設置。  

## VPC構築手順  
① IAMユーザーでログイン。    
②サービスでVPCを選び、「VPCを作成」をクリック。<br>デフォルトでVPCが作成されているが基本的には自身で作成したモノを使う。  
[![Image from Gyazo](https://i.gyazo.com/2b2fa92d8fed4aee1aa8cbfb9317f4e8.png)](https://gyazo.com/2b2fa92d8fed4aee1aa8cbfb9317f4e8)
②必要事項を記入して作成をクリック。ロード後、閉じるボタンが出るので閉じるをクリック。     
* 名前タグ  
* IPv4 CIDR ブロック  
* IPv6 CIDR ブロック  
* テナンシー(物理ハードウェアを占有するオプション。EC2の料金割高になる可能性がある。）
[![Image from Gyazo](https://i.gyazo.com/bf8534cc6a43c7366d5618c4deb2214c.png)](https://gyazo.com/bf8534cc6a43c7366d5618c4deb2214c)
## public&priveteサブネットの作成手順  
① IAMユーザーでログイン。  
②サービスでサブネットを選び、「サブネットの作成」をクリック。<br>デフォルトでサブネットが作成されているが基本的には自身で作成したモノを使う。 
[![Image from Gyazo](https://i.gyazo.com/2662ff4ba7f801df82f1f36f37831f7e.png)](https://gyazo.com/2662ff4ba7f801df82f1f36f37831f7e)
③必要事項を記入して作成をクリック。ロード後、閉じるボタンが出るので閉じるをクリック。<br>※publicもprivateも作り方は同じ。  
* 名前タグ  
* VPC：サブネットを使用するVPCを選択。     
* VPC CIDR  
* アベイラビリティーゾーン  
* IPv4 CIDR ブロック  

[![Image from Gyazo](https://i.gyazo.com/f493ebd49d7831227394dccccfd5a605.png)](https://gyazo.com/f493ebd49d7831227394dccccfd5a605)
## ルーティングの設定  
* 何をするの？<br>→パブリックサブネットからインタネットに接続できるようするための**ルーティング**を設定する。  
※インターネット ← パブリックサブネット（インターネットとから接続。ソフトウェアをインストール。）  
### (補足） IPアドレスとルーティング  
インターネットでは、**ルーターがIPアドレスの行き先を管理している**ので、<br>ネットワークとネットワークがIPアドレスを通じて接続することができる。<br>これを**ルーティング**という。
### ルートテーブルの補足  
ルートテーブルは「宛先のIPアドレス」と「次のルーター（AWSではターゲット）」という書式で設定する。  

|宛先のIPアドレス|次のルーター|
|:----------:|:--------:|
|10.0.1.0/24|local<br>(**自身のネットワーク**)|
|10.0.2.0/24|ルーターB|
|0.0.0.0/0<br>**デフォルトルート**|ルーターC|

※**デフォルトルート**：ルートてブルに登録されている、どのアドレスにも一致しない場合の経路。  
### ルーティングを設定する作業手順  
* インターネットゲートウェイを作成し、VPCにアタッチする。  
※**インターネットゲートウェイ**：VPCとインターネットを繋げる仮想のルーター。  
①サービスでVPC選択し、VPCダッシュボード内のインターネットゲートウェイをクリック。<br>遷移後、「インターネットゲートウェイの作成」をクリック。  
[![Image from Gyazo](https://i.gyazo.com/f07114df889eb5791ed91a9f09307ebf.png)](https://gyazo.com/f07114df889eb5791ed91a9f09307ebf)
②名前を記入して作成をクリック。ロード後、閉じるボタンが出るので閉じるをクリック。  
[![Image from Gyazo](https://i.gyazo.com/2a9ec08fced640cc4bf3e9c87b9a383b.png)](https://gyazo.com/2a9ec08fced640cc4bf3e9c87b9a383b)
③どのVPCにも接続していないので状態が「detached」になっている。
[![Image from Gyazo](https://i.gyazo.com/ee94272ade8a9bb5337b7cd9d0bed8df.png)](https://gyazo.com/ee94272ade8a9bb5337b7cd9d0bed8df)
そのため、作成したルーティングを選択し、アクションタグをクリックしVPCにアタッチをクリック。<br>VPCを選択しアタッチをクリックする。  
[![Image from Gyazo](https://i.gyazo.com/40999ab34b032e6955178697bef021c9.gif)](https://gyazo.com/40999ab34b032e6955178697bef021c9)
[![Image from Gyazo](https://i.gyazo.com/6b4f1da3675e1a1b9c81a0cf59591a8c.png)](https://gyazo.com/6b4f1da3675e1a1b9c81a0cf59591a8c)
* ルートテーブルを作成し、パブリックサブネットに紐付ける。  
①VPCダッシュボード内のルートテーブルをクリック。<br>遷移後、現状のルートテーブルの内容を確認し「ルートテーブルの作成」をクリック。
[![Image from Gyazo](https://i.gyazo.com/a11fc83cb0c05c1e8e97b7a36f7c36eb.png)](https://gyazo.com/a11fc83cb0c05c1e8e97b7a36f7c36eb)
②必要事項を記入＆選択し作成をクリック。ロード後、閉じるボタンが出るので閉じるをクリック。  
[![Image from Gyazo](https://i.gyazo.com/0abb0c7d6a0e3e48a18901119ac3c942.png)](https://gyazo.com/0abb0c7d6a0e3e48a18901119ac3c942)
③publicサブネットとの紐付けを行うため、「サブネットの関連付けの編集」をクリック。<br>publicサブネットを選択し保存をクリック。
[![Image from Gyazo](https://i.gyazo.com/9e89864e2d6d3b530f513dd38d299534.gif)](https://gyazo.com/9e89864e2d6d3b530f513dd38d299534)
④デフォルトルートをインターネットゲートウェイに設定する。<br>public-routeを選択し、ルートタグを選びルートの編集をクリック。
[![Image from Gyazo](https://i.gyazo.com/7646d43cde146ff5b0347fcddd69a157.gif)](https://gyazo.com/7646d43cde146ff5b0347fcddd69a157)
⑤遷移後、ルートの追加をクリックし、送信先を入力し、ターゲットにインターネットゲートウェイを選択しルートを保存をクリック。<br>ロード後、閉じるボタンが出るので閉じるをクリック。  
[![Image from Gyazo](https://i.gyazo.com/2a98fcb7f735a635c4de21ec9008d98b.png)](https://gyazo.com/2a98fcb7f735a635c4de21ec9008d98b)
## ネットワーク設計で気を付ける点  
### VPCの設計のポイント  
* プライベートIPアドレス範囲から指定する。  
VPCでは仮想のプライベートネットワーク空間を作成するので、<br>プライベートIPアドレスの使用が推奨。  

|10.0.0.0 ~ 10.255.255.255|
|:-----------------------:|
|172.16.0.0 ~ 172.31.255.255|
|192.168.0.0 ~ 192.168.255.255|

* 作成後は変更できないので大きめに設定する。<br>（例）大きさは/28から/16。推奨は/16らしい。  
* オンプレミスや他VPCのレンジと重複しないように気を付ける。<br>相互接続する可能性のある場合は重複しないように設計する。  
### VPCを分割する？それともアカウントを分ける？  
* 異なるシステムの場合はアカウントを分ける。<br>異なるシステムを同一アカウントに入れると管理が煩雑になる。  
* 同一システム各環境は、VPCとアカウントどっちに分けるのか？  
・環境が違う場合、アカウントもVPCも同一のモノを使用するのはダメ。  
・VPCを分けると、IAM設定が一度でよい。<br>しかし、各環境のリソースが見えてしまい事故の元となる。  
・アカウントを分けると、他の環境のリソースが見えず作業しやすい。<br>しかし、環境ごとにIAMの設定が必要。  
・同一アカウントで、VPCとリージョンを分ける方法がベターかもしれない。  
### サブネットの設計ポイント  
* 将来に放るようなIPアドレス数を見積もって設計する。/24が標準的  
※/24だと、/16内のVPCにサブネットを２５６個作成でき、1つのサブネットに254個のIPアドレスを作成することができる。   
* サブネットの分割は、ルーティングとアベイラビリティーゾーンを基準に行う。  
・サブネットに割り当てられるルートテーブルは一つ。  
・インターネットアクセスの有無、拠点アクセスの有無などのルーティングポリシーに応じて分割する。  
・高可用性のために2つ以上のアベイラビリティーゾーンを使用する。
