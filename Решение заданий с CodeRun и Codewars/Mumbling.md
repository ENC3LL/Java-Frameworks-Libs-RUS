[[CodeRW]]

На этот раз ни истории, ни теории. В приведенных ниже примерах показано, как написать функцию:`accum`

#### Примеры:

```
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt"
```

# Решение

```java ignore
public class Accumul {  
  
    public static String accum(String s) {  
        if (s == null || s.isEmpty()) {  
            return "";  
        }  
  
        StringBuilder result = new StringBuilder();  
  
        for (int i = 0; i < s.length(); i++) {  
            char currentChar = s.charAt(i);  
  
            result.append(Character.toUpperCase(currentChar));  
  
            for (int j = 0; j < i; j++) {  
                result.append(Character.toLowerCase(currentChar));  
            }  
  
            if (i < s.length() - 1) {  
                result.append("-");  
            }  
        }  
        return result.toString();  
    }  
}
```

# Варианты решения

```java ignore
public class Accumul {
  public static String accum(String s) {
    StringBuilder bldr = new StringBuilder();
    int i = 0;
    for(char c : s.toCharArray()) {
      if(i > 0) bldr.append('-');
      bldr.append(Character.toUpperCase(c));
      for(int j = 0; j < i; j++) bldr.append(Character.toLowerCase(c));
      i++;
    }
    return bldr.toString();
  }
}
```

```java ignore
public class Accumul {
    
    public static String accum(String s) {
      String[] letters = s.toUpperCase().split("");
      for(int i = 0; i < letters.length; ++i){
        letters[i] += letters[i].toLowerCase().repeat(i);
      }
      return String.join("-", letters);
    }
}
```


```java ignore
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class Accumul {
    public static String accum(String s) {
        var chars = s.split("");

        return IntStream.range(0, chars.length)
                .mapToObj(i -> chars[i].toUpperCase() + chars[i].toLowerCase().repeat(i))
                .collect(Collectors.joining("-"));
    }
}
```