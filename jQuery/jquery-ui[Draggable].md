# Draggable  
(例①)自由自在に動く、縦と横方向に動く。
[![Image from Gyazo](https://i.gyazo.com/5c3473f9f3a5bee45b3dfe72c60300ad.gif)](https://gyazo.com/5c3473f9f3a5bee45b3dfe72c60300ad)
```
<!DOCTYPE html>
<html>
  <head>
    <link href="jquery-ui/jquery-ui.css">
      <style>
         #draggable {
          width: 200px;
          height: 100px;
          background-color: blue;
        }
      </style>
  </head>
  <body>
   <div id="draggable">ドラッグして下さい</div>
   <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
   <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>

    <script type="text/javascript">
      //自由にドラッグできる
      // $("#draggable").draggable();
      
      //y軸（縦方向）に動く
      // $( "#draggable" ).draggable({ axis: "y" });

      //x軸（横方向）に動く
      $( "#draggable" ).draggable({ axis: "x" });
    </script>
  </body>
</html>
```
(例②)指定された範囲でドラッグする
[![Image from Gyazo](https://i.gyazo.com/91a71783203c901d9987dbbbe6dfe9d6.gif)](https://gyazo.com/91a71783203c901d9987dbbbe6dfe9d6)
```
<!DOCTYPE html>
<html>
  <head>
    <link href="jquery-ui/jquery-ui.css">
      <style>
         #draggable {
          width: 200px;
          height: 100px;
          background-color: blue;
        }
        #container {
          width: 500px;
          height: 500px;
          background-color: lightblue;
        }
        #draggable2 {
          width: 200px;
          height: 100px;
          background-color: orange;
        }
      </style>
  </head>
  <body>
   <div id="draggable">ドラッグして下さい</div>
    <div id="container">
      <div id="draggable2">指定された範囲内でのみ動きます</div>
    </div>

   <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
   <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>

    <script type="text/javascript">
      $("#draggable").draggable({ axis:"y"});
      //({containment:"parent"})で親要素の範囲内でのみ動くように指定。
      $("#draggable2").draggable({containment:"parent"});
    </script>
  </body>
</html>
```
