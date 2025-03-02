[[CodeRW]]

Когда предоставлен номер между , верните его словами. Обратите внимание, что входные данные гарантированно находятся в диапазоне .`0-9` `0-9`

Ввод: `1`

Выпуск:.`"One"`

Если ваш язык поддерживает эту функцию, попробуйте использовать оператор switch.

# Решение

```java ignore
public class Kata  
{  
    public static String switchItUp(int number)  
    {  
        switch (number){  
            case 1:  
                return "One";  
            case 2:  
                return "Two";  
            case 3:  
                return "Three";  
            case 4:  
                return "Four";  
            case 5:  
                return "Five";  
            case 6:  
                return "Six";  
            case 7:  
                return "Seven";  
            case 8:  
                return "Eight";  
            case 9:  
                return "Nine";  
            case 0:  
                return "Zero";  
            default:  
                return "";  
        }  
    }  
}
```

# Варианты решения

```java ignore
public class Kata
{
  public static String switchItUp(int number)
  {
    switch (number)
    {
      case 0: return "Zero";
      case 1: return "One";
      case 2: return "Two";
      case 3: return "Three";
      case 4: return "Four";
      case 5: return "Five";
      case 6: return "Six";
      case 7: return "Seven";
      case 8: return "Eight";
    }
    return "Nine";
  }
}
```

```java ignore
public class Kata {
  public static String switchItUp(int number) {
    return new String[] {"Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"}[number];
  }
}
```