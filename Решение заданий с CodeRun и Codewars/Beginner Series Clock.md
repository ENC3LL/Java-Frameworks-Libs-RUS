[[CodeRW]]

Часы показывают часы, минуты и секунды после полуночи.`h``m``s`

Ваша задача состоит в том, чтобы написать функцию, которая возвращает время с полуночи в миллисекундах.

## Пример:

```
h = 0
m = 1
s = 1

result = 61000
```

# Решение

```java ignore
public class Clock
{
    public static int Past(int h, int m, int s)
    {
        return (h*3600 + m*60 + s)*1000;
    }
}
```

# Вариант решения

```java ignore
import java.time.Duration;

public class Clock {
  public static int Past(int h, int m, int s) {
    return (int)Duration.ofHours(h).plusMinutes(m).plusSeconds(s).toMillis();
  }
}
```

