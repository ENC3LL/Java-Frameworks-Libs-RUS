[[CodeRW]]

## Задача

Суммируйте все числа заданного массива ( cq. list ), кроме самого большого и самого низкого элемента ( по значению, а не по индексу! ).

Самый высокий или самый низкий элемент соответственно — это один элемент на каждом ребре, даже если существует более одного элемента с одинаковым значением.

Обратите внимание на проверку входных данных.

## Пример

```
{ 6, 2, 1, 8, 10 } => 16
{ 1, 1, 11, 2, 3 } => 6
```

## Валидация входных данных

Если вместо массива задано пустое значение ( , , , и т. д. ) или данный массив является пустым списком или списком только с элементом, возвращаем .`null``None``Nothing``nil``1``0`

# Решение

```java ignore
import java.util.ArrayList;  
  
public class Kata {  
    public static int sum(int[] numbers) {  
        if (numbers == null || numbers.length == 0) {  
            return 0;  
        }  
  
        int max = numbers[0];  
        int min = numbers[0];  
          
        for (int num : numbers) {  
            if (num > max) {  
                max = num;  
            }  
            if (num < min) {  
                min = num;  
            }  
        }  
          
        ArrayList<Integer> filteredList = new ArrayList<>();  
        boolean removedMax = false;  
        boolean removedMin = false;  
  
        for (int num : numbers) {  
            if (num == max && !removedMax) {  
                removedMax = true;  
            } else if (num == min && !removedMin) {  
                removedMin = true;   
            } else {  
                filteredList.add(num);  
            }  
        }  
  
        int sm = 0;  
        for (int num : filteredList) {  
            sm += num;  
        }  
  
        return sm;  
    }  
}
```

# Вариант решения

```java ignore
import java.util.Arrays;

public class Kata
{
  public static int sum(int[] numbers) {
        if(numbers == null || numbers.length <= 2) return 0;
        int sum = 0;
        Arrays.sort(numbers);
        for(int i = 1; i < numbers.length-1; i++){
            sum += numbers[i];
        }
        return sum;
    }
}
```