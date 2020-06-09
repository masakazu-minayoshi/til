# ストロングパラメータ  
* ストロングパラメータは、MassAsignmentの脆弱性を突く攻撃に対処するための仕組み。  
## MassAsignmentの脆弱性を突く攻撃とは？  
フォームが送信するparamsの内容を改ざんするなどして、開発者が意図していないデータをDBに保存させる攻撃。  
> 参考
[ストロングパラメーターについてサクッと解説。](https://qiita.com/Panzo_webengineer/items/b7ea861a429950477568)  
## Chromeでの攻撃手順  
（Pictweetでの例）

・tweetの投稿画面で検証ツールを開く。  
・テキストフィールドのフォームを選択する。  
・表示されたHTMLタグのname属性の内容を変更する。  

[![Image](https://tech-master.s3.amazonaws.com/uploads/curriculums//29c75b76703e1e1b73ad8dadb6eb8133.png)](https://tech-master.s3.amazonaws.com/uploads/curriculums//29c75b76703e1e1b73ad8dadb6eb8133.png)

(想定被害)  
例えば、あるテーブルにadminカラムがあり、そこに1というフラグが立っていたら管理者だという設計になっているとする。    
上記手順でparamsのキーは変更できるので、本来はimageカラムに保存すべき内容をadminカラムに保存させることができる。  
その結果、テキストフィールドに1と入力すれば管理者になりすますことができてしまう。  
だから、ストロングパラメータで悪意をもってキーを書き換えたとしても、想定しているキー以外は弾く仕組みにする。    
