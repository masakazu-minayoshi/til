# AWSとは何？  
* AWS(Amazon Web Services)はAmazon社が提供する**クラウドサービス**。  
* 100以上のサービスが存在し、クラウドサービスとして世界最大規模である。  
## AWSの特徴  
①サービスが豊富  
* EC2やRDSなど100以上のサービスが存在している。  
* 高負荷に耐えられる、信頼性の高いシステムを少ない手間で運用できる。  
②リソースが柔軟  
* リソースを必要な時に必要な分だけ調達できる。  
（例）繁忙期の時だけサーバーを増やす。  
③従量課金  
* 使った分だけ支払う従量課金なので費用対効果が優れている。  
## マネジメントコンソール  
* マネジメントコンソール：ログイン後に表示されるAWSの管理画面。  

### IAMユーザー  
* AWSアカウントを作成するとルートユーザーが作成される。<br>**ルートユーザーは普段使用せず、<br>作業用のIAMユーザーを使用するのがAWSのベストプラクティス**。  

|ルートユーザー|作業用ユーザー<br>(IAMユーザー)|
|:--------:|:-------------------------|
|そのアカウントの全てのAWSユーザーと<br>AWSリソース全てに完全なアクセス権を持つユーザー|AWSで作成するユーザー|
|アカウントの変更、解約サポートプランの<br>変更などをするときのみ使用する。|作業者ごとに個別に作成する|
|極力ルートユーザーを使用しない|通常作業はIAMユーザーで行う|

### CloudTrail  
* **CloudTrail**:**いつ誰が何をしたのか記録しておく**ことができる。<br>不正アクセスや不正操作があった時にチェックできる。  
* 設定方法：CloudTrailで認証を作成する。  
* S3にログが保存することで、ずっと保存ができる。  
* デフォルトで有効になっているが保存期間は90日のみ。  
* CloudTrail自体は無料だがS3の料金は発生。  
