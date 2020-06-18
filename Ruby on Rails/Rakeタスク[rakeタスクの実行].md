# 問題  
Railsで、定期的に実行したい処理は、lib/tasks以下のディレクトリに、rakeタスクを作成して処理を記述することが多い。  
次のコードは、全てのユーザーに対して。ユーザーが入店したかどうかを管理する<br>"enterd_flag"というカラムをfalseにするrakeタスクです。  
rakeタスクの使い方を確認した上で、下記のrakeタスクを、ターミナルから実行するためには、<br>どのようなコマンドを実行すればいいか、答えてください。  
```
lib/tasks/user_checker.rb

namespace :user do
  desc "ユーザーの入店情報をリセットする"
  task reset_entered_flag: :environment do
    User.update_all(entered_flag: false)
  end
end
```

[回答]  
rakeタスク実行コマンド  
```
$ rake user:reset_entered_flag
```
[補足]  
* rake [namespeceの名前]:[taskの名前]のように記述して実行する。  
毎日・毎週特定の曜日・３日おきなど、特定の周期でrakeタスクを自動実行したい場合は、  
[wheneverというgemを組み合わせて利用する。](https://morizyun.github.io/blog/whenever-gem-rails-ruby-capistrano/index.html)

* Rakeタスクファイルを生成コマンド
```
$ rails g task task_sample
```
* タスクに処理を実装(ブロック内に処理を追加します)  
```
[lib/tasks/task_sample.rake]
namespace :task_sample do
  desc "実行処理の説明"
  task :sample do
    puts "Hello World"
  end
end
```




> 参考  
[RailsでRakeタスクの作成](https://qiita.com/suzuki-koya/items/787b5562d2ae1a215d94)  
[Rails における rake タスクの :environment について](https://qiita.com/FumiyaShibusawa/items/11035fc640bb36a615ad)  

