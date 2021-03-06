# IAMとは何？  
* IAM：**AWSのサービスを利用するユーザー権限を管理するサービス**。  
【概要】  
* AWSリソースをセキュア（安全）に操作するために、認証・認可の仕組みを提供する。  
* 各AWSリソースに対して別々のアクセス権限をユーザーごとに付与できる。  
* AWS IAM自体の利用は無料。  
【用語】  
* ポリシー：アクセス許可の定義。<br>「どのAWSサービスの」「どのリソースに対して」「どんな操作を」「許可する（許可しない）」を定義。  
* ユーザー：ここのアカウントのユーザー  
* グループ：IAMユーザーの集合。複数のユーザーにアクセス許可を付与する作業を簡素化。  
* ロール：一時的にアクセスを許可したアカウントを発行できる。<br>EC2やLambdaなどのAWSリソースに権限を付与するために使用。  
[![Image from Gyazo](https://i.gyazo.com/36c71f7a778b9052dc0ff5217f28a352.png)](https://gyazo.com/36c71f7a778b9052dc0ff5217f28a352)
## IAMのベストプラクティス  
* 個々人にIAMユーザーを作成させる。  
* ユーザーをグループに所属させ、グループに権限を割り当てる。  
* 権限は最小限にする。  
* EC２インスタンスから実行するアプリケーションにはロールを使用する。  
* 定期的に不要な認証情報を削除する。  

