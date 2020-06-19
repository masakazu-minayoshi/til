# アソシエーションにおけるclass_nameの定義  
## 問題  
下記のEventモデルには、Userモデルの関係が定義されています。  
現在は@event.userのような形で、@eventに紐づいたuserを取得することができます。  
アソシエーションのメソッド名とクラス名が一致している時はそれで問題ありませんが、  
メソッド名を変えたいこともあります。  
EventモデルとUserモデルの関係を、@event.ownerと  
記述して取得できるようにするためのコードを記述して下さい。   
```
[app/models/event.rb]
class Event < ActiveRecord::Base
  belongs_to :user
  has_many :tickets

  validates :name, length: { maximum: 50 }, presence: true
  validates :place, length: { maximum: 100 }, presence: true
  validates :content, length: { maximum: 2000 }, presence: true
  validates :start_time, presence: true
  validates :end_time, presence: true
  validate :start_time_should_be_before_end_time

  def created_by?(user)
    return false unless user
    owner_id == user.id
  end

  private

  def start_time_should_be_before_end_time
    return unless start_time && end_time

    if start_time >= end_time
      errors.add(:start_time, 'は終了時間よりも前に設定してください')
    end
  end
end
```
[回答]
```
class Event < ActiveRecord::Base
//belongs_to :userを以下に書き換える
  belongs_to :owner, class_name: 'User'
```
上記記述で、@tweet.ownerのような形で、@tweetに紐づいたuserレコードを取得することができる。  
## class_nameオプションとは？  
* 関連を設定するモデルクラス名を指定できる。  
* (利用場面) 関連名と参照先のクラス名を異なるものにしたい場合に指定する。  
* 一つのモデルに対して、二つのアソシエーション経路を組む場合に多用します。  

## コード例  
関連名から関連相手のオブジェクト名を生成できない事情がある場合、<br>:class_nameオプションを用いてモデル名を直接指定できます。  
例えば、1人の著者(author)が複数の書籍(books)を持っているが、<br>実際の書籍モデル名がTransactionである場合には以下のように指定します。
```
class Author < ApplicationRecord
  has_many :books, class_name: "Transaction"
end
```




> 参照  
[railsアソシエーションオプションのメモ](https://qiita.com/tomoharutt/items/e548186c763079327ed1)  
[アソシエーションにおけるclass_nameの定義！](https://qiita.com/wacker8818/items/eccdf0a63616feb14a70)  
[Railsガイド:Active Record の関連付け](https://railsguides.jp/association_basics.html)  






