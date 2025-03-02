[[CodeRW]]

Просто, если задана строка слов, возвращает длину самого короткого слова (слов).

Строка никогда не будет пустой, и вам не нужно учитывать разные типы данных.

# Решение

```java ignore
public class Kata {  
    public static int findShort(String s) {  
        String[] words = s.split(" ");  
        String small = words[0];  
  
        for (String word : words) {  
            if (small.length() > word.length()){  
                small = word;  
            }  
        }  
        return small.length();  
    }  
}
```

# Варианты решения

```java ignore
import java.util.stream.*;
public class Kata {
    public static int findShort(String s) {
        return Stream.of(s.split(" "))
          .mapToInt(String::length)
          .min()
          .getAsInt();
    }
}
```

```java ignore
import java.util.Arrays;

public class Kata {
    public static int findShort(String s) {
        return Arrays.stream(s.split(" ")).mapToInt(String::length).min().getAsInt();
    }
}
```