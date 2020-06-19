# 問題  
整数を要素に持つ配列の中で、「奇数の要素」と「偶数の要素」の和をそれぞれ求め、出力します。
```
class Main {
  public static void main(String[] args) {
    // 変数numbersに、与えられた数字の配列を代入してください
    int[] numbers = {1, 4, 6, 9, 13, 16};
    
    int oddSum = 0;
    int evenSum = 0;
    
    // for文を用いて、配列numbersの偶数の和と奇数の和を求めてください
    for (int number: numbers) {
      if (number % 2 == 0) {
        evenSum += number;
      } else {
        oddSum += number;
      }
    }

    System.out.println("奇数の和は" + oddSum + "です");
    System.out.println("偶数の和は" + evenSum + "です");
  }
}
```

> 参考  
[令和元年(から)のプログラミング](https://reiwa55.blog.fc2.com/blog-entry-8.html)  
