# 外部ライブラリのimport  
## xx外部ライブラリの読み込み  
* 外部ライブラリを自分のプログラムに読み込む（使えるようにする）ためにimportを用いる。  
```
(例）外部ライブラリの読み込み
[Main.java]
//外部ライブラリを読み込む
import java.lang.Math;
class Main {
  public static void main(String[] args) {
  
  }
}
```
## 外部ライブラリ読み込みの例②
```
[Main.java]
import java.lang.Math;
class Main {
  public static void main(String[] args) {
    //外部から読み込んだMathメソッド
    int max = Math.max(3, 8);
    System.out.println("最大値は" + max + "です");
  }
}
>出力結果
最大値は８です
```
* Mathクラスのmaxメソッドを使用する。  
※maxメソッドは2つの数値のうち大き方を返す。  
