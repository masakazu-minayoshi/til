# Scannerクラスの使い方  
```
import java.util.Scanner;

public class Exercise6 {
  public static void main(String[] args) {
      System.out.println("数字を入力して下さい。");
      // scannerクラスのインスタンスを作成
      // 引数で標準入力System.inを指定する
      Scanner scanner1 = new Scanner(System.in);
      //int型で受け取りたい時はnextInt();
      int x = scanner1.nextInt();

      System.out.println("文字を入力して下さい");

      Scanner scanner2 = new Scanner(System.in);
      //String型で受け取りたい時はnextLine();
      String str = scanner2.nextLine();

      System.out.println(x);
      System.out.println(str);
  }
}

>出力結果
数字を入力して下さい。
24
文字を入力して下さい
good
24
good

```


> 参考  
[Scannerクラスの使い方！Javaで標準入力を取得する方法【初心者向け】](https://techacademy.jp/magazine/19080)  
