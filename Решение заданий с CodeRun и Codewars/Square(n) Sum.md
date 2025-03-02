[[CodeRW]]

Завершите функцию квадратной суммы так, чтобы она возвела в квадрат каждое переданное в нее число, а затем суммировала результаты.

Например, для него должно возвращаться, потому что `[1, 2, 2]` `9` 
1^2+2^2+2^2=9.

# Решение

```java ignore
public class Kata  
{  
    public static int squareSum(int[] n) {  
        int sum = 0;  
        for (int num : n){  
            sum += num *num;  
        }  
        return sum;  
    }  
}
```

# Вариант решения

```java ignore
import java.util.Arrays;

public class Kata {
  public static int squareSum(int[] xs) {
    return Arrays.stream(xs).map(x -> x * x).sum();
  }
}
```

