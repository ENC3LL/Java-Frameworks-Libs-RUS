[[CodeRW]]

При наличии строки необходимо вернуть строку, в которой каждый символ (с учетом регистра) повторяется один раз.

### Примеры (ввод -> вывод):

```
* "String"      -> "SSttrriinngg"
* "Hello World" -> "HHeelllloo  WWoorrlldd"
* "1234!_ "     -> "11223344!!__  "
```

# Решение

```java ignore
public class Solution{  
    public static String doubleChar(String s){  
        StringBuilder result = new StringBuilder();  
  
        for( char c : s.toCharArray()){  
            result.append(c).append(c);  
        }  
        return result.toString();  
    }  
}
```

# Вариант решения

```java ignore
public class Solution{
  public static String doubleChar(String s){
     return s.replaceAll(".", "$0$0");
  }
}
```