# キーボードから整数を 5回入力し、大きい順に並べ替えて表示するプログラムを作成しなさい。<br>ただし、配列を用いて実装すること  

```

import java.util.Scanner;


public class Array5 {
    public static void main(String[] args) {
          //整数型配列の定義
          int[] aNum = new int[5];
          //オブジェクトのインスタンス化
          Scanner sc = new Scanner(System.in);

          //整数を入力
          for(int i = 0; i < 5; i++){
              aNum[i] = sc.nextInt();
          }

          //バブルソート
          for(int i = 1; i < 5; i++) {
              for(int j = 4; j >= i; j--) {
                  if(aNum[j] > aNum[j-1]) {
                      //バブルソートアルゴリズム
                      aNum[j] = aNum[j] ^ aNum[j-1];
                      aNum[j-1] = aNum[j] ^ aNum[j-1];
                      aNum[j] = aNum[j] ^ aNum[j-1];
                  }
              }
          }
          System.out.println("");
          //出力
          for(int i = 0; i < 5; i++) {
              System.out.println(aNum[i]+"");
          }
    }

}
>出力結果
1
2
3
4
5

5
4
3
2
1
```


> 参考  
[要素数を取得する](http://www.creative-forest.com/java/java_intro/array/element/element.html)  
[【Java】キーボード入力を受け付ける2つの方法【BufferedReader & Scanner】](https://reasonable-code.com/java-keyboard-input/)  
[【プロが解説】Java配列の基礎はこれで完璧！便利な使い方も多数紹介](https://www.sejuku.net/blog/84946)  
[5.配列:練習問題](http://kitako.tokyo/lib/JavaExercise.aspx?id=105)  
[Javaでキーボードからランダムに10個の整数を入力して昇順にソートするサンプルプログラム](http://arkgame.com/?p=24998)  

