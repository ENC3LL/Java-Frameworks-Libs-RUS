[[CodeRW]]

Завершите метод, принимающий логическое значение, и верните строку для  для ."Yes" ``true`` "No" ``false

# Решение

```java ignore
class YesOrNo {  
    public static String boolToWord(boolean b) {  
        if (b==true) {  
            return "Yes";  
        } else {  
            return "No";  
        }  
    }  
}
```

# Вариант решения

```java ignore
class YesOrNo
{
  public static String boolToWord(boolean b)
  {
    return b ? "Yes" : "No";
  }
}
```

