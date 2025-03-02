[[CodeRW]]

Ваши одноклассники попросили вас скопировать для них какие-то документы. Вы знаете, что есть «n» одноклассников, а в документах «m» страниц.

Ваша задача — рассчитать, сколько пустых страниц вам нужно. Если или вернуть .`n < 0` `m < 0` `0`

### Пример:

```
n= 5, m=5: 25
n=-5, m=5:  0
```

# Решение

```java ignore
public class Paper  
{  
    public static int paperWork(int n, int m)  
    {  
        if (n <= 0 || m <= 0){  
            return 0;  
        } else {  
            return n * m;  
        }  
    }  
}
```

# Вариант решения

```java ignore
public class Paper
{
  public static int paperWork(int n, int m) 
  {
    return (n < 0) || (m < 0) ? 0 : n * m;
  }
}
```