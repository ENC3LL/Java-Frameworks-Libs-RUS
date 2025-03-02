[[CodeRW]]

Рассмотрите массив/список овец, в которых некоторые овцы могут отсутствовать на своем месте. Нам нужна функция, которая подсчитывает количество овец, присутствующих в массиве (true означает присутствующих).

Например

```csharp
[true,  true,  true,  false,
  true,  true,  true,  true ,
  true,  false, true,  false,
  true,  false, false, true ,
  true,  true,  true,  true ,
  false, false, true,  true]
```

Правильный ответ будет .`17`

Подсказка: Не забудьте проверить наличие плохих значений, таких как `null`/`undefined`

# Решение

  
```java ignore
public class Counter {  
    public static int countSheeps(Boolean[] arrayOfSheeps) {  
        int count = 0;  
        for (Boolean sheep : arrayOfSheeps) {  
            if (Boolean.TRUE.equals(sheep)) {  
                count++;  
            }  
        }  
        return count;  
    }  
}
```

# Вариант решения

```java ignore
import java.util.Arrays;
import java.util.Collections;

public class Counter {
  public int countSheeps(Boolean[] arrayOfSheeps) {
    return Collections.frequency(Arrays.asList(arrayOfSheeps), true);
  }
}
```

