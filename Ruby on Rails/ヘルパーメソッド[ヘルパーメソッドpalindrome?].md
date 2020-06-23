# 問題  
以下の手順でRailsアプリケーションを作成し、仕様にしたがって機能を追加してください。
```
> cd ~/projects/
> rails new reverse-app -d mysql
> cd reverse-app/
> rails g scaffold item name:string
> bundle exec rake db:create
> bundle exec rake db:migrate
```
仕様
```
・登録されたitemのnameが回文（上から読んでも下から読んでも同じになる文）なのかを判定するヘルパーメソッドpalindrome?を作成してください。
・ヘルパーメソッドは、回文だった時は「回文です」そうでない時は「回文ではありません」という文字列を返すものとします。
・一覧表示画面で、以下のようにその結果を表示させるようにしてください。
```
[![Image from Gyazo](https://i.gyazo.com/c1252b2918c57ccdce8cfc1cdf3d1b56.png)](https://gyazo.com/c1252b2918c57ccdce8cfc1cdf3d1b56)

## 回答  
[items_helper.rb]
```
module ItemsHelper
  def palindrome?(word)
    word == word.reverse ? "回文です" : "回文ではありません"
  end
end
```
[index.html.erb]
```
<p id="notice"><%= notice %></p>

<h1>Items</h1>

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th colspan="3"></th>
    </tr>
  </thead>

  <tbody>
    <% @items.each do |item| %>
      <tr>
        <td><%= item.name %></td>
        //追記
        <td><%= palindrome?(item.name) %></td>
        
        <td><%= link_to 'Show', item %></td>
        <td><%= link_to 'Edit', edit_item_path(item) %></td>
        <td><%= link_to 'Destroy', item, method: :delete, data: { confirm: 'Are you sure?' } %></td>
      </tr>
    <% end %>
  </tbody>
</table>

<br>

<%= link_to 'New Item', new_item_path %>

```

> 参考  
[Ruby on Rails チュートリアル](https://railstutorial.jp/chapters/rails_flavored_ruby?version=4.2)  
[]()  

