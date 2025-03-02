[[CodeRW]]
Напишите функцию, которая принимает неотрицательное целое число и строку в качестве параметров и возвращает строку, повторяющуюся точно по разам.`n``s``s``n`

### Примеры (ввод -> вывод)

```
6, "I"     -> "IIIIII"
5, "Hello" -> "HelloHelloHelloHelloHello"
```

# Решение

```java ignore
public class Solution {
    public static String repeatStr(final int repeat, final String string) {

        String repeated = string.repeat(repeat);

        return repeated;
    }
}

```

# Вариант решения

```java ignore
class Solution {
  static String repeatStr(int repeat, String string) {
    return string.repeat(repeat);
  }
}
```