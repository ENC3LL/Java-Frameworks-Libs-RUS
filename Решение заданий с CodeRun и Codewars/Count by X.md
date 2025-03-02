[[CodeRW]]

Создайте функцию с двумя аргументами, которая будет возвращать массив первых кратных . `n` `x`

Предположим, что и данное число, и количество подсчетов будут положительными числами больше . `0`

Верните результаты в виде массива или списка (в зависимости от языка).

### Примеры

```
x = 1, n = 10 --> [1,2,3,4,5,6,7,8,9,10]
x = 2, n = 5  --> [2,4,6,8,10]
```

# Решение

```java ignore
public class Kata{  
    public static int[] countBy(int x, int n){  
        int[] array = new int[n];  
  
        // Заполняем массив значениями, кратными x  
        for (int i = 0; i < n; i++) {  
            array[i] = x * (i + 1); // Каждый элемент равен x * (индекс + 1)  
        }  
  
        return array;  
    }  
}
```

# Вариант решения

```java ignore
import java.util.stream.IntStream;

public class Kata{
  public static int[] countBy(int x, int n){
    
    return IntStream.rangeClosed(1, n)
      .map(i -> i * x)
      .toArray();
  }
}
```