[[CodeRW]]

# Суммирование

Напишите программу, которая находит суммирование каждого числа от 1 до числа. Число всегда будет положительным целым числом больше 0. Вашей функции нужно только вернуть результат, в примере ниже показано, как вы достигаете этого результата, и он не является его частью, см. примеры тестов.

Например **(Вход -> Выход):**

```
2 -> 3 (1 + 2)
8 -> 36 (1 + 2 + 3 + 4 + 5 + 6 + 7 + 8)
```

# Решение
( ∑ = 0,5 n × (n+1) ) - сумма n членов натурального ряда

```java ignore
public class GrassHopper {  
    public static int summation(int n) {  
        double sum;  
        sum = (0.5*n)*(n+1);  
        return (int) sum;  
    }  
}
```

#  Вариант решения

```java ignore
import java.util.stream.IntStream;

public class GrassHopper {
    public static int summation(int n) {
        return IntStream.rangeClosed(1,n).sum();
    }
}
```