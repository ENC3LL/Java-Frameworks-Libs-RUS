[[CodeRW]]

Напишите функцию, которая принимает строку из одного или нескольких слов и возвращает ту же строку, но со всеми словами, содержащими пять или более перевернутых букв (точно так же, как название этой Ката). Передаваемые строки будут состоять только из букв и пробелов. Пробелы будут включаться только в том случае, если присутствует более одного слова.

Примеры:

```
"Hey fellow warriors"  --> "Hey wollef sroirraw" 
"This is a test        --> "This is a test" 
"This is another test" --> "This is rehtona test"
```

# Решение

```java ignore
public class SpinWords {  
  
    public String spinWords(String sentence) {  
        String[] words = sentence.split(" ");  
  
        for (int i = 0; i < words.length; i++) {  
            if (words[i].length() >= 5) {  
                words[i] = new StringBuilder(words[i]).reverse().toString();  
            }  
        }  
  
        return String.join(" ", words);  
    }  
}
```

# Варианты решения

```java ignore
public class SpinWords {

  public String spinWords(String sentence) {
    
       for (String a : sentence.split(" "))
       {
           if (a.length()> 4)
           {
              sentence = sentence.replace(a, new  StringBuffer(a).reverse());
           }
       }
       return sentence;
  }
}
```

```java ignore
import java.util.stream.*;
import java.util.Arrays;

public class SpinWords {

  public String spinWords(String sentence) {
    return Arrays.stream(sentence.split(" "))
                 .map(i -> i.length() > 4 ? new StringBuilder(i).reverse().toString() : i)
                 .collect(Collectors.joining(" "));
  }
}
```

