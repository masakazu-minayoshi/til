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
```
import java.util.Scanner;

public class Sample {
  public static void main(String[] args) {
    // Scannerクラスのインスタンスを作成
    // 引数で標準入力System.inを指定する
    Scanner scanner = new Scanner(System.in);
    // 入力を促すメッセージ
    System.out.print("入力してください > ");
    //入力された内容をインスタンスから取得
    String input_text = scanner.nextLine();
    //入力された内容を画面に表示
    System.out.println(input_text + "が入力されました");
    // Scannerクラスのインスタンスをクローズ
    scanner.close();
  }
}
>出力結果
入力してください > おはよう
おはようが入力されました
```


> 参考  
[Scannerクラスの使い方！Javaで標準入力を取得する方法【初心者向け】](https://techacademy.jp/magazine/19080)  
[Javaプログラミング追加問題61-90記事一覧](http://javakunren.49ch.net/category13/)  


