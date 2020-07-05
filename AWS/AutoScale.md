# AutoScale  
## AutoScale(オートスケール)とは？  
* アプリケーションの負荷を処理するために適切な数の<br>AmazonEC2インスタンスを利用できるように準備することができる。  
* 必要な時に必要な数のインスタンスを用意することができる。  
* 時間帯によるアクセス数の増減が大きかったり予測ができない場合に役立つ。  
[![Image from Gyazo](https://i.gyazo.com/bdc96446825a3d251987c23c6f4e4a9e.png)](https://gyazo.com/bdc96446825a3d251987c23c6f4e4a9e)
* CPU使用率やトラフィック量を事前に設定しておいた値を超えたらインスタンス台数が増え、<br>その値より下がったら起動するインスタンス台数を減らすといった挙動ができます。  
* AutoScaleでは外部からのアクセスはまずはELBで受けるため、ユーザはその配下のインスタンス台数を意識する必要ない。  

## AutoScale設定例  
[注意]  
* 課金はEC2インスタンスやELBの利用として発生する。  
### 起動設定の作成  
* EC2→Auto Scaling グループ→Auto Scaling グループの作成をクリック
[![Image from Gyazo](https://i.gyazo.com/a2589f59fe147f59e368c01af569ddc7.png)](https://gyazo.com/a2589f59fe147f59e368c01af569ddc7)
### 「今すぐ始める」をクリック
[![Image from Gyazo](https://i.gyazo.com/1a54a98ab8293cb6d667e9e99fda42a6.png)](https://gyazo.com/1a54a98ab8293cb6d667e9e99fda42a6)
### AutoScaleで利用するAMIの「選択」をクリック   
[![Image from Gyazo](https://i.gyazo.com/d3a8e2b34761a1ce9f0d3a7bc287108d.png)](https://gyazo.com/d3a8e2b34761a1ce9f0d3a7bc287108d)
### インスタンスサイズを選択し、「次の手順：詳細設定」  
[![Image from Gyazo](https://i.gyazo.com/d3f40c2f4cab58a1d0f51dc247bf0d5e.png)](https://gyazo.com/d3f40c2f4cab58a1d0f51dc247bf0d5e)
### 設定名を入力して「確認画面にスキップ」をクリック  
[![Image from Gyazo](https://i.gyazo.com/a21aa3b2b98eaf0831891378e0d09504.png)](https://gyazo.com/a21aa3b2b98eaf0831891378e0d09504)
※上記は名前を「sampleAS」と設定した場合。  
### 設定内容を確認し、問題なければ「起動設定の作成」をクリック  
[![Image from Gyazo](https://i.gyazo.com/14fb0947980238a0cb0d61cbcd0f85ed.png)](https://gyazo.com/14fb0947980238a0cb0d61cbcd0f85ed)
### EC2インスタンスで利用するキーペアを選択して「起動設定の作成」をクリック  
* EC2インスタンス作成時と同様に行う。  
[![Image from Gyazo](https://i.gyazo.com/84e6e498a13d8838d657f2e8e264e6fa.png)](https://gyazo.com/84e6e498a13d8838d657f2e8e264e6fa)
### AutoScalingグループの作成  
* 設定値を入力してから「スケーリングポリシーの設定」をクリック。  
[![Image from Gyazo](https://i.gyazo.com/5357f7c84c7be3ece9d9e3334bfdd1b9.png)](https://gyazo.com/5357f7c84c7be3ece9d9e3334bfdd1b9)
※上記では sampleAS-01 というグループ名に、その他VPCやサブネット、ELBを使う場合はその設定等を行っている。  
### 「このグループを初期のサイズに維持する」→「次の手順：通知の設定」を選ぶ。  
* EC2インスタンスに障害が発生してシャットダウンしても、自動的に1台起動する設定する作業である。  
* この結果、いつでも必ず1台のEC2インスタンスが動いている状態を作り出すことで、<br>サービス全体が停止する状態を防ぐことができる。  
* AutoScaleの発動条件や起動するEC2インスタンスの最大数を設定したい場合は、<br>もう一つの「スケーリングポリシーを使用して・・・」の方を選ぶ。
[![Image from Gyazo](https://i.gyazo.com/8db4e4cc7a83d76dec779c84fafd8ce9.png)](https://gyazo.com/8db4e4cc7a83d76dec779c84fafd8ce9)
### 通知に必要な設定値を入力して「次の手順：タグを設定」をクリック  
* AutoScaleが動いた時の通知設定をする。  
* 「通知の送信先」は設定名を、「受信者」の欄には実際に存在するメールアドレスなど、<br>通知するイベント種類をチェックする。
[![Image from Gyazo](https://i.gyazo.com/08984a44cb4f1f52e0c0dbca98fffba4.png)](https://gyazo.com/08984a44cb4f1f52e0c0dbca98fffba4)
### 必要に応じてタグの設定をしてから「確認」をクリック  
* タグの設定は任意なので、未設定でも問題ない。必要に応じて設定する。  
[![Image from Gyazo](https://i.gyazo.com/3609e37a9beaca31dd21e2920abae1b6.png)](https://gyazo.com/3609e37a9beaca31dd21e2920abae1b6)
### 設定値を確認して問題なければ「Auto Scalingグループの作成」をクリック
[![Image from Gyazo](https://i.gyazo.com/ad40d089df5fafff8c3a6f4a6705d9fd.png)](https://gyazo.com/ad40d089df5fafff8c3a6f4a6705d9fd)
### 「閉じる」をクリックして作業終了。
[![Image from Gyazo](https://i.gyazo.com/afd2b3502797e5e7d59f1ef860d0f93a.png)](https://gyazo.com/afd2b3502797e5e7d59f1ef860d0f93a)




