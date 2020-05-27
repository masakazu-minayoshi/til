# 聖杯デザイン (Grid)  
## Gridのメリット  
* HTMLの不要なdivがどんどん消えていく。  
* CSSのgridの中にある子要素がシンプルになる。  
* レスポンシブデザインの時にgrid-templateだげ書き換えれば良い。  
* 余白もgrid-templateで指定することができるので視覚的に分かりやすい。  
```
[HTML]
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <link rel="stylesheet" href="style.css" />
    </head>
    <body>
        <header>header</header>
        <nav>left</nav>
        <main>center</main>
        <aside>right</aside>
        <footer>footer</footer>
    </body>
</html>
```
```
[CSS]
body {
  font-size: 2rem;
  width: 800px;
  margin: 0 auto;
  min-height: 100vh;
  display: grid;
  grid-template:
      /* gritテンプレート内で外周と要素間の余白を指定することができる */
      "... ...... ...... ...... ...... ...... ..."
      "... header header header header header ..." 150px
      "... ...... ...... ...... ...... ...... ..."
      "... left   ...... center ...... right  ..." 1fr
      "... ...... ...... ...... ...... ...... ..."
      "... footer footer footer footer footer ..." 300px
      "... ...... ...... ...... ...... ...... ..."
      / auto 150px auto 1fr auto 200px auto;
      /* 要素間の余白をとる
      gap: 10px; */
}
header {
  grid-area: header;
}
main {
  grid-area: center;
}
nav {
  grid-area: left;
}
aside {
  grid-area: right;
}
footer {
  grid-area: footer;
}
@media screen and (max-width: 1000px) {
  body {
      grid-template:
          "header" 150px
          "center" 1fr
          "left  "
          "right "
          "footer" 300px;
  }
}
```


> 引用
[【HTML/CSSレイアウト】Gridを使うとFlexboxより簡単に複雑なレイアウトを組めます](https://www.youtube.com/watch?v=cwkkD0ejX8Q&list=PLwM1-TnN_NN5x6_-OTH9BFVgbYg_l7oEN&index=4)
