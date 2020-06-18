# 問題  
Railsアプリケーションのコントローラーに関して以下のコードをみてください。
```
class ApplicationController < ActionController::Base
  before_action :configure_permitted_parameters , if: :devise_controller?

  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_up, keys: [:nickname, :avatar])
  end
end
```
このコードが何を実現しているのか説明してください。  
特に、この記述がApplicationControllerクラスに書いてあることに留意し、どのような動作になるのか解説を行なって下さい。

[回答]  
* ApplicationControllerを継承しているコントローラー（ranking, users, およびdevise用のコントローラー）内の<br>全てのアクションが実行される前に、before_actionが実行される。
* もし、それがdeviseのコントローラーだったら（devise_controller?というメソッドの返り値がtrueだったら）<br>configure_permitted_parametersを呼ぶ。
* configure_permitted_parametersの中で、<br>devise_parameter_sanitizerの記載はストロングパラメータのdevise版。  
* サインアップ時に、nicknameとavatarカラムへの保存を許可する。  
初期設定の段階では、メールアドレスとパスワードのみを受け取るように設定ので、<br>新しいキーをコントローラに受け取らせるためには、<br>ストロングパラメーターを編集しなければならない。  


[補足]  
deviseのコントローラーは、デフォルトではアプリケーション内に作成されない。  
GitHubでソースコードを確認するとdeviseのコントローラーがApplictaionControllerを継承していることが確認できる。  


> 参考  
[before_actionとストロングパラメーターの編集について](https://qiita.com/okamoto_ryo/items/52e3506e06c27631395e)    
[rails 発展その2 ログイン機能](https://qiita.com/savaniased/items/a7ee3cf1cd6dab4755e0)  
