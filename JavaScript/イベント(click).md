# clickイベント   
（例）「金メダル、銀メダル、銅メダルをクリックしたら消える。」  


[![Gyazo gif](https://gyazo.com/32f9ee3b907e301dbb69e2da8b772971.gif)](https://gyazo.com/32f9ee3b907e301dbb69e2da8b772971)


```html:sample.html
<!DOCTYPE html>
<html>
  <head>
    <title>Javascript</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <div id="gold-medal" class="medal"></div>
    <div id="silver-medal" class="medal"></div>
    <div id="bronze-medal" class="medal"></div>
    <script type="text/javascript" src="test.js"></script>
</body>
</html>
```

```css:style.css
body {
  font-family: Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
}
#gold-medal {
  background-color: #DBB400;
}
#silver-medal {
  background-color: #C9CACA;
}
#bronze-medal {
  background-color: #C47022;
}
.medal {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  float: left;
  margin: 20px;
}
```


```test.js
//document.getElementById("").onclickでクリックしたターゲットの要素を取得。
//function(){ }でドッキリの内容を記載
//document.getElementById("").style.display = "none";でドッキリの内容が記載されている。

//（1行目）金メダルをクリックするとイベントが発生。 ← （2行目）金メダルのCSS要素にdisplya: none;が追加される。
document.getElementById("gold-medal").onclick = function(){
  document.getElementById("gold-medal").style.display = "none";
  }
//（1行目）銀メダルをクリックするとイベントが発生。 ← （2行目）銀メダルのCSS要素にdisplya: none;が追加される。
  document.getElementById("silver-medal").onclick = function(){
    document.getElementById("silver-medal").style.display = "none";
  }
//（1行目）銅メダルをクリックするとイベントが発生。 ← （2行目）銅メダルのCSS要素にdisplya: none;が追加される。
  document.getElementById("bronze-medal").onclick = function(){
    document.getElementById("bronze-medal").style.display = "none";
  }
```

> 引用
[Qiita](https://qiita.com/minakichi/items/0d2073aea6a5d4541bb2)
