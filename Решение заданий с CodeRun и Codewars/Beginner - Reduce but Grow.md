[[CodeRW]]

Если дан непустой массив целых чисел, возвращает результат умножения значений по порядку. Пример:

```
[1, 2, 3, 4] => 1 * 2 * 3 * 4 = 24
```

# Решение

```java ignore
public class Kata{  
    public static int grow(int[] x){  
        int sum = 1;  
        for(int num : x){  
            sum *= num;  
        }  
        return sum;  
    }  
}
```

# Вариант решения

```java ignore
import java.util.*;

public class Kata{
  public static int grow(int[] x){
    return Arrays.stream(x).reduce(1 ,(a, b) -> a * b);
  }
}
```