[[CodeRW]]

Завершите решение так, чтобы оно перевернуло переданную в него строку.

```
'world'  =>  'dlrow'
'word'   =>  'drow'
```

# Решение

```java ignore
public class Kata {  
  
    public static String solution(String str) {  
        return new StringBuilder(str).reverse().toString();  
    }  
  
}
```

