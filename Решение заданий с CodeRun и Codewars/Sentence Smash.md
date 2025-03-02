[[CodeRW]]

Напишите функцию, которая берет массив слов, разбивает их в предложение и возвращает предложение. Вы можете игнорировать любую необходимость в очистке слов или добавлении знаков препинания, но вы должны добавить пробелы между каждым словом. **Будьте внимательны, в начале или в конце предложения не должно быть пробела!**

## Пример

```
['hello', 'world', 'this', 'is', 'great']  =>  'hello world this is great'
```

```java ignore
words = ['hello', 'world', 'this', 'is', 'great']
smash(words) # returns "hello world this is great"
```

## Предположения

- Вы можете предположить, что вам даны только слова.
- Вы не можете предполагать размер массива.
- Вы можете предположить, что у вас есть массив.

## Что мы тестируем

Мы тестируем базовые циклы и манипуляции со строками. Это для новичков, которые только изучают циклы и манипуляции со строками.

## Отказ

Это для новичков, поэтому мы хотим протестировать базовые циклы и манипуляции со строками. Продвинутые пользователи должны легко сделать это в одной строке.


# Решение
  
```java ignore
public class SmashWords {  
    // Метод для объединения слов  
    public static String smash(String[] words) {  
        //добавляем стринг билдер  
        StringBuilder stringBuilder = new StringBuilder();  
        for (int i = 0; i < words.length; i++) {  
            if (i>0) {  
                stringBuilder.append(" "); //добавляем после каждого слова пробел  
            }  
            stringBuilder.append(words[i]);  
        }  
        return stringBuilder.toString(); // Возвращаем объединенную строку  
    }  
    
    public static void main(String[] args) {  
        //массив  
        String[] words = { "hello", "world", "this", "is", "great" };  
        String result = smash(words); // Вызываем метод smash  
        System.out.println(result); // Выводим результат  
    }  
}
```


# Вариант решения

```java ignore
public class SmashWords {
	public static String smash(String... words) {
    return String.join(" ", words);
  }
}
```