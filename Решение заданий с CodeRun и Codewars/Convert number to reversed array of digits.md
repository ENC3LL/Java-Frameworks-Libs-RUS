[[CodeRW]]

Если дано случайное неотрицательное число, вы должны вернуть цифры этого числа в массиве в обратном порядке.

### Пример (вход = > выход):

```
35231 => [1,3,2,5,3]
0     => [0]
```

# Решение

```java ignore
public class Kata {
    public static int[] digitize(long n) { // Изменяем тип параметра на long
        // Преобразуем число в строку
        String numberStr = Long.toString(n); // Используем Long.toString для long
        // Создаем массив для хранения цифр в обратном порядке
        int[] result = new int[numberStr.length()];
        
        // Проходим по строке с конца к началу и заполняем массив
        for (int i = 0; i < numberStr.length(); i++) {
            result[i] = Character.getNumericValue(numberStr.charAt(numberStr.length() - 1 - i));
        }
        
        return result;
    }
}
```

# Вариант решения

```java ignore
public class Kata {
  public static int[] digitize(long n) {
        return new StringBuilder().append(n)
                                  .reverse()
                                  .chars()
                                  .map(Character::getNumericValue)
                                  .toArray();
  }
}
```