# Accordion  
(例①)アコーディオン  
[![Image from Gyazo](https://i.gyazo.com/3ed5d605658bdd207544ed629ee22c07.gif)](https://gyazo.com/3ed5d605658bdd207544ed629ee22c07)
```
<!DOCTYPE html>
<html>
  <head>
    <link href="jquery-ui/jquery-ui.css">
    <style>
    </style>
    </head>
    <body>
      <div id="accordion">
        <h3>Section1</h3>
        <div>
          <p>あいうえお</p>
        </div>
          <h3>Section2</h3>
        <div>
          <p>かきくけこ</p>
        </div>
      </div>

      <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
      <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
  <script type="text/javascript">
    $("#accordion").accordion();
  </script>
  </body>
</html>

```

(例②)sortable  
[![Image from Gyazo](https://i.gyazo.com/3be0c23039e5db715ef360006c150df8.gif)](https://gyazo.com/3be0c23039e5db715ef360006c150df8)
```
<!DOCTYPE html>
<html>
  <head>
    <link href="jquery-ui/jquery-ui.css">
      <style>
      </style>
    </head>
    <body>
      <ul id="sortable">
          <li>カレーライス</li>
          <li>パスタ</li>
          <li>親子丼</li>
          <li>海鮮丼</li>
          <li>酢豚</li>
      </ul>

    <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
    <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
    <script type="text/javascript">
        $("#sortable").sortable();
    </script>
  </body>
</html>
```
> 引用
[jQuery ui](https://jqueryui.com/accordion/)
